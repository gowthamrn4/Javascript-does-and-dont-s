---


---

<pre><code>              **JAVA Script Best Practices**
</code></pre>
<ol>
<li>Place Scripts at the Bottom of Your Page</li>
</ol>
<p><code>&lt;p&gt;And now you know my favorite kinds of corn. &lt;/p&gt;</code><br>
<code>&lt;script type``="text/javascript" src="path/to/file.js"&gt;&lt;/``script``&gt;</code><br>
<code>&lt;script</code>type``=“text/javascript”<code>src="path/to/anotherFile.js"&gt;&lt;/script&gt;</code><br>
<code>&lt;/body&gt;</code><br>
<code>&lt;/html&gt;</code></p>
<ol start="2">
<li>Declare Variables Outside of the For Statement</li>
</ol>
<h4 id="bad">Bad</h4>
<p>When executing lengthy “for” statements, don’t make the engine work any harder than it must. For example:</p>
<p><code>for (var</code> <code>i = 0; i &lt; someArray.length; i++) {</code><br>
<code>var</code> <code>container = document.getElementById('container');</code><br>
<code>container.innerHtml +'my number: '+ i;</code><br>
<code>console.log(i);</code><br>
<code>}</code></p>
<h4 id="better">Better</h4>
<p><code>var container = document.getElementById('container');</code><br>
<code>for(var i = 0, len = someArray.length; i &lt; len; i++) {</code><br>
<code>container.innerHtml +='my number: '+ i;</code><br>
<code>console.log(i);</code><br>
<code>}</code></p>
<p>3.The Fastest Way to Build a String</p>
<p>Don’t always reach for your handy-dandy “for” statement when you need to loop through an array or object. Be creative and find the quickest solution for the job at hand.</p>
<pre><code>`var arr = ['item 1','item 2','item 3', ...];`

`varlist ='&lt;ul&gt;&lt;li&gt;'+ arr.join('&lt;/li&gt;&lt;li&gt;') +'&lt;/li&gt;&lt;/ul&gt;';`
</code></pre>
<ol start="5">
<li>Reduce Globals</li>
</ol>
<p>By reducing your global footprint to a single name, you significantly reduce the chance of bad interactions with other applications, widgets, or libraries.</p>
<p><strong>Bad</strong></p>
<pre><code>`var name =`Jeffrey';`

`var lastName ='Way';`

`function doSomething() {...}`

`console.log(name);// Jeffrey -- or window.name`
</code></pre>
<h4 id="better-1">Better</h4>
<pre><code>`var DudeNameSpace = {`

`name :'Jeffrey',`

`lastName :'Way',`

`doSomething :function``() {...}`

`}`
</code></pre>
<p><code>console.log(DudeNameSpace.name);</code> <code>// Jeffrey</code></p>
<ol start="6">
<li>Comment Your Code</li>
</ol>
<p>It might seem unnecessary at first, but trust me, you WANT to comment your code as best as possible. What happens when you return to the project months later, only to find that you can’t easily remember what your line of thinking was. Or, what if one of your colleagues needs to revise your code? Always, always comment important sections of your code.</p>
<pre><code>// Cycle through array and echo out each name.
    `for``(``var` `i = 0, len = array.length; i &lt; len; i++) {`
    
    `console.log(array[i]);`
    
    `}`
</code></pre>
<ol start="7">
<li>
<p>Don’t Pass a String to “SetInterval” or “SetTimeOut”</p>
<p><code>setInterval(</code><br>
<code>"document.getElementById('container').innerHTML += 'My new number: ' + i"``, 3000</code><br>
<code>);</code><br>
Not only is this code inefficient, but it also functions in the same way as the “eval” function would. <strong>Never pass a string to SetInterval and SetTimeOut.</strong> Instead, pass a function name.</p>
<p>setInterval(someFunction, 3000);</p>
</li>
<li>
<p>Don’t Use the “With” Statement</p>
</li>
</ol>
<p>At first glance, “With” statements seem like a smart idea. The basic concept is that they can be used to provide a shorthand for accessing deeply nested objects. For example…</p>
<pre><code>`with` `(being.person.man.bodyparts) {`
`arms =` `true``;`
`legs =` `true``;`
`}`

-- instead of --
</code></pre>
<p><code>being.person.man.bodyparts.arms =</code> <code>true``;</code><br>
<code>being.person.man.bodyparts.legs=</code> <code>true``;</code></p>
<p>9.Use {} Instead of New Object()</p>
<p>There are multiple ways to create objects in JavaScript. Perhaps the more traditional method is to use the “new” constructor, like so:</p>
<p><strong>Bad</strong></p>
<pre><code>`var` `o =` `new` `Object();`
`o.name =` `'Jeffrey'``;`
`o.lastName =` `'Way'``;`
`o.someFunction =` `function``() {`
`console.log(``this``.name);`
`}`
</code></pre>
<p><strong>Better</strong></p>
<pre><code>`var` `o = {`
`name:` `'Jeffrey'``,`
`lastName =` `'Way'``,`
`someFunction :` `function``() {`
`console.log(``this``.name);`
`}`
`};`
</code></pre>
<p>10.Use [] Instead of New Array()</p>
<p><strong>Bad</strong></p>
<pre><code>`var` `a =` `new` `Array();`
`a[0] =` `"Joe"``;`
`a[1] =` `'Plumber'``;`
</code></pre>
<p><strong>Better</strong></p>
<p><code>var a = ['Joe','Plumber'];</code></p>
<ol start="11">
<li>Long List of Variables? Omit the “Var” Keyword and Use Commas Instead</li>
</ol>
<p><strong>Bad</strong><br>
<code>var</code> <code>someItem =</code> <code>'some string'``;</code><br>
<code>var</code> <code>anotherItem =</code> <code>'another string'``;</code><br>
<code>var</code> <code>oneMoreItem =</code> <code>'one more string'``;</code></p>
<p><strong>Better</strong></p>
<pre><code>`var` `someItem =` `'some string'``,`
`anotherItem =` `'another string'``,`
`oneMoreItem =` `'one more string'``;`
</code></pre>
<ol start="13">
<li>Always, Always Use Semicolons</li>
</ol>
<p>Technically, most browsers will allow you to get away with omitting semi-colons.</p>
<p><strong>Bad</strong><br>
<code>var</code> <code>someItem =</code> <code>'some string'</code><br>
<code>function</code> <code>doSomething() {</code><br>
<code>return</code> <code>'something'</code><br>
<code>}</code><br>
<strong>Better</strong></p>
<pre><code>`var` `someItem =` `'some string'``;`
`function` `doSomething() {`
`return` `'something'``;`
`}`
</code></pre>
<p>14.Avoid globals</p>
<p>lobal variables and function names are an incredibly bad idea. The reason is that every JavaScript file included in the page runs in the same scope. If you have global variables or functions in your code, scripts included after yours that contain the same variable and function names will overwrite your variables/functions.</p>
<p>There are several workarounds to avoid using globals — we’ll go through them one by one now. Say you have three functions and a variable like this:<br>
<strong>Bad</strong></p>
<pre><code>   var current = null;
    function init(){...}
    function change(){...}
    function verify(){...}
</code></pre>
<p><strong>Better</strong></p>
<pre><code>var myNameSpace = {
  current:null,
  init:function(){...},
  change:function(){...},
  verify:function(){...}
}
</code></pre>
<ol start="15">
<li>Use shortcut notation when it makes sense</li>
</ol>
<p><strong>Bad</strong></p>
<pre><code> var cow = new Object();
    cow.colour = 'brown';
    cow.commonQuestion = 'What now?';
    cow.moo = function(){
      console.log('moo');
    }
    cow.feet = 4;
    cow.accordingToLarson = 'will take over the world';
</code></pre>

