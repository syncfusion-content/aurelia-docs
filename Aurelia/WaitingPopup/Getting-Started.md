---
layout: post
title: Getting-Started | WaitingPopup | JavaScript | Syncfusion
description: getting started
platform: Aurelia
control: WaitingPopup
documentation: ug
keywords: ejwaitingpopup, waitingpopup, js waitingpopup 
---

# Getting Started

This section explains briefly about how to create a **WaitingPopup** in your application with **JavaScript**.
**Essential JavaScript WaitingPopup** provides support to display a **WaitingPopup** within your webpage. From the following guidelines, you can learn how to create a **WaitingPopup** in a real-time login page authentication scenario. 

The following screenshot illustrates the functionality of a **WaitingPopup** with login page scenario.

![](/js/WaitingPopup/Getting-Started_images/Getting-Started_img1.png) 

You can give the Username and Password in the **login page**. When you click the **Login** button, you get the **WaitingPopup**. After loading, the alert box pops up with the message “Signed in successfully”.

## Create Username and Password

 * To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started).
* Create `WaitingPopup` folder inside `src/samples` location.
* Create `WaitingPopup.html` file inside  `src/samples/WaitingPopup` folder and use the below code for rendering RichTextEditor component 


{% highlight html %}

<template>
  <require from="./default-functionalities.css"></require>
  <div>
    <div id="targetElement">
      <table class="loginTable">
        <tr>
          <td>Username</td>
          <td><input type="text"/></td>
        </tr>
        <tr>
          <td>Password</td>
          <td><input type="password"/></td>
        </tr>
        <tr>
          <td></td>
          <td><button id="btnOpen" class="e-btn" ej-button="e-text:Login; size: medium, type: button, height: 30, width: 150"
          e-on-click.trigger="onOpen()"></button></td>
        </tr>
      </table>
      <div id="popup" class="waiting" ej-waiting-popup></div>
    </div>
</template>

{% endhighlight %}

Initialize the WaitingPopup in script

* Create `WaitingPopup.js` file inside `src/samples/WaitingPopup` folder with below code snippet.

{% highlight js %}

export class DefaultFunctionalities { }

{% endhighlight %}

{% highlight css %} 

<style type="text/css" class="cssStyles">
   #targetElement {
       width: 500px;
       height: 200px;
       margin: 50px;
       border: 1px solid #dbdcdb;
   }
   .loginTable {
       margin: 60px auto;
   }
   #popup_WaitingPopup .e-image {
       display: block;
       height: 70px;
   }
</style>


{% endhighlight %}


The following screenshot displays a **User** **login**.


![](/js/WaitingPopup/Getting-Started_images/Getting-Started_img2.png) 

## Add WaitingPopup Widget

To render the ejWaitingPopup using aurelia directive, we need to inject the ej aurelia directive with modules.

 In a real-time login page scenario, when you click the Login button, the WaitingPopup is displayed. 

{% highlight js %}

export class DefaultFunctionalities { 
 constructor() {}
 onOpen(args) {
	 $("#popup").ejWaitingPopup({
                showOnInit: true,
                target: "#targetElement"
            });
            function success() {
                let obj = $("#popup").data("ejWaitingPopup");
                alert("Signed in successfully");
                obj.hide();
            }
			setTimeout(success, 5000);
             
}
}

{% endhighlight %}

 The following screenshot shows the output of the above code example.

![](/js/WaitingPopup/Getting-Started_images/Getting-Started_img3.png) 

