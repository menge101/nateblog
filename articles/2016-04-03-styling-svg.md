---
title: Styling SVG
date: 03/04/2016

An unexpected opportunity to learn something new occurred with my need for a logo for this blog.

The logo is an SVG file, embedded in the html.  I could have left the 'styling' of the image embedded as well, however 
instead I chose to pull out the styling to my primary site css file, and assign classes to the elements of the svg.

    <svg xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg" version="1.1" width="7...
      <g transform="translate(124.47968,180.36612)">
        <path class="x-wrench" d="m-12.16 483.52c-18.81-2.66-38.78-10.57-51.98-20.59-22.81-17.31-36.35-4...
      </g>
      <g transform="translate(124.47968,180.36612)">
        <path class="logo-fill" d="M131.49 242.01 17.88 128.33 73.56 72.05 129.24 15.77l116.24 0.03 116...
      </g>
      <g transform="translate(124.54171,177.15243)">
        <path class="logo-lines" d="M239.9 371.6C237.76 370.01 183.01 315.66 118.25 250.84L0.5 132.96c0-2...
      </g>
    </svg>

You can see above the 'paths' of the svg have three different components.  The logo consists of the lines for the gem,
the background color for the gem, and the wrenches; which are an area colored and 'stroked'.

The following CSS is applied to the logo:

    .logo-lines {
      fill: #ffffff;
      image-rendering:auto;
    }
    
    .logo-fill {
      fill: #ff0000;
    }
    
    .x-wrench {
        fill: #ff0000;
        stroke-linecap: round;
        stroke-linejoin: round;
        stroke-width: 15;
        stroke: #ffffff;
    }
    
This makes for a simple but easily modified logo.  
![Original](http://i.imgur.com/brfVo3h.png)
    
A simple modification of the CSS to this:  

    .logo-lines {
      fill: #ff0fff;
      image-rendering:auto;
    }
    
    .logo-fill {
      fill: #0000ff;
    }
    
    .x-wrench {
        fill: #00ff00;
        stroke-linecap: round;
        stroke-linejoin: round;
        stroke-width: 15;
        stroke: #000000;
    } 
    
Makes an image that looks like this:      
![Altered](http://i.imgur.com/q8lajzX.png)