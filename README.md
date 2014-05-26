MultiNestedLists
================

A jQuery plugin for multiple nested lists

Looking up the internet, there were no solutions for my need, of having a nice style for multiple nested lists. I needed of a style that could evidence every <kbd>ul</kbd> inside of a <kbd>li</kbd>. The idea was to use nested lists to aplly in sitemaps, org charts and things like that. I have seen so many interesting solutions on the internet, like <kbd>ul</kbd> based in trees, sitemap examples, but not even one of these solutions would serve for my simple need. I just needed something like this: 
<pre><code class="bash">bootstrap/
├── css/
│   ├── bootstrap.css
│   ├── bootstrap.min.css
│   ├── bootstrap-theme.css
│   └── bootstrap-theme.min.css
├── js/
│   ├── bootstrap.js
│   └── bootstrap.min.js
└── fonts/
    ├── glyphicons-halflings-regular.eot
    ├── glyphicons-halflings-regular.svg
    ├── glyphicons-halflings-regular.ttf
    └── glyphicons-halflings-regular.woff
</code></pre>

Accordind some requirements I had, this structure should be composed dynamically, because new <kbd>ul</kbd> and <kbd>li</kbd> can be created any time by the user. Therefore, I couldn't use any class or id in <kbd>ul</kbd> or <kbd>li</kbd>. The structure needed to be clean. 
<pre><code class="bash">ul
├── li -> ul
│   ├── li                  
│   ├── li                   
│   ├── li                   
│   └── li /ul
│   /li                    
├── li -> ul                       
│   ├── li                   
│   └── li /ul
│   /li                
└── li -> ul                 
    ├── li                 
    ├── li                 
    ├── li                        
    └── li /ul
    / li                    
/ul
</code></pre>
All this seemed like too simple, and I was decided clearly to make this just with CSS. I decided add <kbd>border-left</kbd> in each <kbd>ul</kbd> and create pseudo-elements to show the indicating lines to each <kbd>li</kbd>. This seemed to be enough, but wasn't! If in any level of the list, the last <kbd>li</kbd> had children, the parent <kbd>ul</kbd> shows its border in its whole height, showing something meaningless. As if there was one more li that doesn't appears. I tried fix this just with css, but there was no advance. Therefore, I started to think how to make it better with jQuery. Then, the solution was: Instead to set <kbd>border-left</kbd> in the <kbd>ul</kbd>, set <kbd>border-left</kbd> in the <kbd>li</kbd> children and check if in each level, the last <kbd>li</kbd> child has children. If yes, take the <kbd>border-left</kbd> off. If no, let it just how it is. This worked! 