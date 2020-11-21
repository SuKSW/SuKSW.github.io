---
layout: post
title:  "Paper.js with Meteor"
date:   2017-04-20
categories: javascript, Meteor, paper-full.js, Paper.js, paperjs.org
---
Some code snippets to draw a path using [paper.js][paperjs] with [meteor][meteor-site].

The directory structure showing only the files that needs to be edited or added:
{% highlight java %}
directory 
	|
	|_ client
	|	  |_ main.js
	|	  |_ pathPage.html
	|
	|_ imports
		  |_ paper-full.js
		  |_ drawPath.js
	
{% endhighlight %}

main.js  
{% highlight javascript %}
import '/imports/paper-full.js';
import '/imports/drawPath.js';
{% endhighlight %}

pathPage.html
{% highlight html %}
{% raw %}
<template name="pathPage">
<h1>Path</h1>
{{> pathCanvasTemplate}}
</template>
 
<template name="pathCanvasTemplate">
        <canvas id="pathCanvas" width="500" height="500"></canvas>
</template>
{% endraw %}
{% endhighlight %}

drawPath.js
{% highlight javascript %}
Template.pathPage.rendered = function() {
    if(!this._rendered) {
        this._rendered = true;
        makeCanvasReady();
    }
}
 
function makeCanvasReady(){
    canvasPath = document.getElementById('pathCanvas');
    canvasPath.addEventListener("mousedown", startThePath,false);
    canvasPath.addEventListener("mouseup", finishThePath,false);
}
 
var paper = require('./paper-full.js');
var path;
function startThePath(event){
    canvasPath = document.getElementById('pathCanvas');
    paper.setup(canvasPath);
    if (path) {
            path.selected = false;
    }
 
    canvasPath.addEventListener("mousemove", drawPath,false);
 
    // Create a new path and set its stroke color to blue:
    path = new paper.Path({
        segments: [getMousePos(canvasPath, event)],
        strokeColor: 'blue',
        strokeWidth: 10,
        strokeCap: 'round',
        // Select the path, so we can see its segment points:
        fullySelected: true
    });
}
 
function drawPath(event){
    path.add(getMousePos(canvasPath, event));
}
 
function finishThePath(){
    canvasPath = document.getElementById('pathCanvas');
    canvasPath.removeEventListener("mousemove",drawPath);
 
        // When the mouse is released, simplify it:
        path.simplify(10);
 
        // Select the path, so we can see its segments:
        path.fullySelected = true;
 
}
 
function getMousePos(canvas, evt) {
  var rect = canvas.getBoundingClientRect();
  return {
    x: evt.clientX - rect.left,
    y: evt.clientY - rect.top
  };
}
{% endhighlight %}


[paperjs]: http://paperjs.org/examples/path-simplification/
[meteor-site]:   https://www.meteor.com/