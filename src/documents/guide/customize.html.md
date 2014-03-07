---
layout: 'docpad_en'
title: 'Customize'
page: 'customize'
needHelp: true
toc: 
 - name: 'How to Customize CSS in Onsen UI'
   href: '#customize-css'
 - name: 'How to Customize Onsen UI Elements'
   href: '#customize-elements'
---

<h2 id="customize-css">How to Customize CSS in Onsen UI</h2>

<p>We are going to show you how to customize the CSS used in Onsen UI.</p> 

<h3>1. Overview of Customizing Onsen UI</h3>

<p>
As with general Web pages, Onsen UI's styles are formatted using CSS.
As a result, you can easily change the styles by overwriting the CSS style that you want to change.
Since Onsen UI is built on Topcoat, CSS references class names from Topcoat.
You will use these class names to customize the CSS in Onsen UI.
</p>

<h3>2. How to Customize</h3>

<h4>Understanding Naming Conventions of Classes</h4>

<p>
Topcoat uses BEM naming conventions including class names. 
Let's take a look at how the classes are named for the components you want to change.
</p>

<p>
As an example, the classes for "Button" are named as shown below:
</p>

<ul>
	<li>topcoat-button (standard size button) </li>
	<li>topcoat-button--large (large size button) </li>
	<li>topcoat-button--large--cta (large size CTA button)</li>
	<li>topcoat-button-hover (standard size button in action status) </li>
</ul>

<p>
For more class names please refer to <a href="/docs/">Docs</a>.
</p>

<h4>Overriding Classes</h4>

<p>
Once you find out the class names of the component you want change, you will override these classes.
Override the classes you want to change in a CSS file you created beforehand.
</p>

<p>
For example, this is how to override if you want to apply a blue (#0000ff) color to the button’s background color.
</p>

<pre><code class="css">.topcoat-button {
  background-color:  #0000ff;
}
</code></pre>

<p>
As you can see, this is exactly how you would change a style on a Web page.
</p>

<h3>3. Customizing a Sample</h3>

<p>
We are going to customize a button in this example.
First, edit the normal style of the button.
Go to the Onsen UI Docs at <a href="http://onsenui.io/docs">http://onsenui.io/docs</a>.
Next, edit the CSS in "Show code snippets" of the "ons-button" section as below:
</p>

<p>Before editing:</p>

<pre><code>.topcoat-button {
  color: #fff;
  background-color: #f2bc00; 
  border: none;
  border-radius:  30px;
}
</pre></code>

<p>After editing:</p>

<pre><code>.topcoat-button {
  color:  #CEDDE5;
  background-color:  #195D7F; 
  border:  none;
  border-radius:  30px;
}
</code></pre>

<p>Next, edit the style when the button is pressed.
Edit the CSS as below, just as you did with the normal style:
</p>

<p>Before editing:</p>

<pre><code>.topcoat-button:active {
  background-color:  #2895CC;
}
</code></pre>

<p>After editing:</p>

<pre><code>.topcoat-button:active {
  background-color: #2895CC;
}
</code></pre>

<p>Save this CSS, and reference it from the html file in Onsen UI. 
Then it will look like the image as below:
The left is the normal style, and the right is the style when the button is pressed.</p>

<p><img src="/images/customize/onsen-css-button-def.png"> <img src="/images/customize/onsen-css-button-hover.png"></p>


<h3>4. Creating Your Own Theme</h3>

<p>We showed you just one example here, but you can edit more components by following these same steps.
Let's try to make your own theme!</p>

<p>Share your original themes with the Onsen UI Team. We are always happy to see new themes from the community!
If you are willing to add your themes to the Onsen UI collection, please refer to the "Contributing" section from the link below, and send a pull request.</p>

<p><a href="https://github.com/OnsenUI/topcoat">https://github.com/OnsenUI/topcoat</a></p>

<hr>

<h2 id="customize-elements">How to Customize Onsen UI Elements</h2>

<p>Because Onsen UI is built on AngularJS, you can edit the templates of each component.
This allows you to customize the existing Onsen UI components to your own style.
We are going to show you how to customize these Onsen UI elements.</p>

<h3>1. Getting Started</h3>

<p>In order to customize Onsen UI elements, you will need to clone a template file from the Onsen UI project in GitHub, edit the template file, and then build it again.</p>

<p>* Please note that you need to install <a href="http://nodejs.org" target="_blank">Node.js</a> before customizing.</p>

<p>First, clone a project from the Onsen UI project in GitHub, and create the project locally. </p>

<p><a href="https://github.com/OnsenUI/OnsenUI">https://github.com/OnsenUI/OnsenUI</a></p>

<pre><code class="bash">$ git clone git@github.com:OnsenUI/OnsenUI.git</code></pre>

<p>Next, execute the "npm install" command in the root folder of the newly created Onsen UI project, and install the required modules.</p>

<pre><code class="bash">$ npm install</code></pre>


<h3>2. How to Edit the Onsen UI Components</h3>

<p>The template files of the Onsen UI components are located in the framework/template directory.
When you are ready to begin editing, go to the framework/template directory, open the template file you want to edit, and replace the html code.</p>

<p>* Please note that changing the structure may cause errors.</p>

<p>This example will show you how to edit and add a style that applies only to the left label on &lt;ons-radio-button&gt; as shown below:</p>

<pre><code>OnsenUI/framework/templates</code></pre>

<p>Before editing:</p>

<pre><code>&lt;label class="topcoat-radio-button"&gt;
	{{leftLabel}}
	&lt;input type="radio" name="{{name}}" ng-model="ngModel" value="{{value}}"&gt;
	&lt;div class="topcoat-radio-button__checkmark"&gt;&lt;/div&gt;
	{{rightLabel}}
&lt;/label&gt;
</code></pre>

<p>After editing:</p>

<pre><code>&lt;label class="topcoat-radio-button"&gt;
	&lt;div class=”style”&gt;
		{{leftLabel}}
&lt;/div&gt;
	&lt;input type="radio" name="{{name}}" ng-model="ngModel" value="{{value}}"&gt;
	&lt;div class="topcoat-radio-button__checkmark"&gt;&lt;/div&gt;
	{{rightLabel}}
&lt;/label&gt;
</code></pre>

<p>This will allow you to apply different styles to the left label when using <ons-radio-button>.</p>

<p>Likewise, you can customize other components by editing the html code in the template files.</p>

<p>After you have completed the editing, execute the "grunt" command, and build the customized Onsen UI project.</p>

<pre><code class="bash">$ grunt</code></pre>

<p>When the project has been successfully built, the customized Onsen UI file will be generated in the build folder.</p>

<p><img src="/images/customize/ons-struct.png" title="Onsen UI directory structure"></p>

<h3>3. How to Apply the Customized Onsen UI to Your Project</h3>

<p>To enable the customized Onsen UI, move all of the newly created files from the build folder to the Onsen UI library folder of the project (the one in which you are using Onsen UI), overwriting the old ones in the process.</p>
