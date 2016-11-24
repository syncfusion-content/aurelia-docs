---
layout: post
title: Getting-Started
description: getting started
platform: aurelia
control: Tile
documentation: ug
---

# Getting Started

This section helps you to understand the getting started of the Tile component with the step-by-step instructions.

## Create a Tile

To create Aurelia Tile component, please refer the common [getting started](https://help.syncfusion.com/aurelia/overview#getting-started) documentation.

Create `tile` folder inside `src/samples` location.

Create `tile.html` file inside `src/samples/tile` folder and use the below code for rendering Tile component.

  {% highlight html %}
  
    <div id="scrollTarget">
           <div class="e-tile-column">
                 <ej-tile id="tile" e-caption.bind="caption" e-tile-size="medium" e-image-url='http://js.syncfusion.com/ug/web/content/tile/map.png'>
                 </ej-tile>
           </div>
     </div>

    {% endhighlight %}
    
Create `tile.js` file inside `src/samples/tile` folder with below code snippet.

    {% highlight javascript %}

       export class BasisUse {
           constructor() {
               this.caption = {text: 'Map' };
           }
       }

    {% endhighlight %}

Get the following output from the above mentioned code

![](Getting-Started_images/Getting-Started_img1.png)

You can easily design a home page using tile component for easy navigation. Therefore, you require many different sizes of tiles aligned in a grid-like manner. The tiles will be aligned automatically to define the necessary tile elements inside the wrapper element, that contains a column class. You can define all columns elements under the wrapper element with the tile group class to make ‘n’ number of tiles as a grouped tile. Add the below mentioned code to the corresponding view page.

{% highlight html %}
    
     <div id="scrollTarget">
                    <div class="e-tile-group">
                        <div class="e-tile-column">
                            <ej-tile id="tile1" e-image-position="fill" e-caption.bind="caption1" e-tile-size="medium" e-image-url='http://js.syncfusion.com/ug/web/content/tile/people_1.png'>
                            </ej-tile>
                            <div class="e-tile-small-col-2">
                                <ej-tile id="tile2" e-image-position="center" e-tile-size="small" e-image-url='http://js.syncfusion.com/ug/web/content/tile/alerts.png'>
                                </ej-tile>
                                <ej-tile id="tile3" e-image-position="center" e-tile-size="small" e-image-url='http://js.syncfusion.com/ug/web/content/tile/bing.png'>
                                </ej-tile>
                                <ej-tile id="tile4" e-tile-size="small" e-image-url='http://js.syncfusion.com/ug/web/content/tile/camera.png'>
                                </ej-tile>
                                <ej-tile id="tile5" e-tile-size="small" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/messages.png'>
                                </ej-tile>
                            </div>
                            <ej-tile id="tile6" e-tile-size="medium" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/games.png' e-caption.bind="caption2">
                            </ej-tile>
                            <ej-tile id="tile7"  e-tile-size="medium" e-image-url='http://js.syncfusion.com/ug/web/content/tile/map.png' e-caption.bind="caption3">
                            </ej-tile>
                            <ej-tile id="tile8"  e-tile-size="wide" e-image-url='http://js.syncfusion.com/ug/web/content/tile/sports.png' e-caption.bind="caption4" e-image-position="fill">
                            </ej-tile>
                        </div>
                        <div class="e-tile-column">
                            <ej-tile id="tile9"  e-tile-size="medium" e-image-position="fill" e-image-url='http://js.syncfusion.com/ug/web/content/tile/people_2.png'  e-caption.bind="caption5">
                            </ej-tile>
                            <ej-tile id="tile10" e-tile-size="medium" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/pictures.png' e-caption.bind="caption6">
                            </ej-tile>
                            <ej-tile id="tile11"  e-tile-size="wide" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/weather.png' e-caption.bind="caption7">
                            </ej-tile>
                            <ej-tile id="tile12" e-tile-size="medium" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/music.png' e-caption.bind="caption8">
                            </ej-tile>
                            <ej-tile id="tile13" e-tile-size="medium" e-image-position="center" e-image-url='http://js.syncfusion.com/ug/web/content/tile/favs.png' e-caption.bind="caption9">
                            </ej-tile>
                        </div>
                    </div>
                </div>
            </div>
    
{% endhighlight %}

{% highlight javascript %}

 export class BasisUse {
  constructor() {
    this.caption1 = {text: 'People' };
    this.caption2 = {text: 'Play' };
    this.caption3 = {text: 'Maps' };
    this.caption4 =  {text: 'Sports' };
    this.caption5 =  {text: 'Peoples' };
    this.caption6 =  {text: 'Photo' };
    this.caption7 =  {text: 'Weather' };
    this.caption8 =  {text: 'Music' };
    this.caption9 = {text: 'Favorites' };
  }
}

{% endhighlight %}

Run the above code to get the following output.

![](Getting-Started_images/Getting-Started_img2.png)

## Template support with Tile Widget  

To customize the Tile images with template feature by using imageTemplateId property of Tile component. Add the below mentioned code to the corresponding view page.

{% highlight html %}

                <div class="e-tile-group" id="groupTile">
                      <div class="e-tile-column">
                          <ej-tile id="tile" e-caption.bind="caption" e-tile-size="wide" e-image-position="fill" e-image-template-id="imageTemplate">
                          </ej-tile>
                          </div>
                          <div id="imageTemplate">
                              <div id="appimage">
                              </div>
                              <div class="tileMargin">
                                  <span class="caption">Google Search</span><br />
                                  <span class="description">The world’s information</span><br />
                                  <span class="sub">Free</span>
                              </div>
                          </div>
                  </div>
   
{% endhighlight %}

{% highlight javascript %}

export class BasisUse {
   constructor() {
    this.caption = {text: 'Windows Store' }; 
  }
}

{% endhighlight %}

Add the following styles to customize the tile images with template support.

{% highlight html %}

 <style>
        #appimage {
            background-image: url("http://js.syncfusion.com/UG/mobile/content/google.png");
            background-position: center center;
            background-repeat: no-repeat;
            background-size: 50% auto;
            display: table-cell;
            width: 45%;
        }

        .tileMargin {
            display: table-cell;
            padding-top: 25px;
        }

        .e-tile-template {
            display: table;
            height: 100%;
            width: 100%;
        }
    </style>
   
{% endhighlight %}

Run the above code to get the following output.

![](Getting-Started_images/Getting-Started_img3.png)

N> _Note:_ _You can find the Tile component properties from the_ [API reference](https://help.syncfusion.com/api/js/ejtile) _document_
