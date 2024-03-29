---
layout: post
title: Getting Started with Aurelia ProgressBar Control | Syncfusion
description: Learn here all about getting started with Syncfusion Essential Aurelia ProgressBar control, its elements, and more.
platform: Aurelia
control: ProgressBar
documentation: ug
keywords: ejprogressbar, progressbar, js progressbar
---

# Getting Started with Aurelia ProgressBar

This section briefly describes how to create a **ProgressBar** control using **Javascript** and learn its features.
**Essential JavaScript** **ProgressBar** displays a **ProgressBar** within a webpage that allows you to show the progress of an event. Here, you can learn how to customize the progress and color of the **ProgressBar** in a real-time application to indicate the strength of the password, where the progress changes with respect to the change in length of the password. This helps you to validate the password is typed. 

The following screenshot shows the **ProgressBar.**

![](/js/ProgressBar/Getting-Started_images/Getting-Started_img1.png) 

## Create a ProgressBar

* To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
* Create `ProgressBar` folder inside `src/samples` location.
* Create `progressbar.html` file inside  `src/samples/progressbar` folder and use the below code for rendering RichTextEditor component 

  
{% highlight html %}

<template>
  <require from="./default-functionalities.css"></require>
  <div style="content-container-fluid">
    <div class="row">
      <div class="cols-sample-area">
        <div class="frame">
          <div class="wrap_up">
            <!--Initializing password field*-->
            <label for="startButton">Password</label>
            <input type="password" id="password" keypress.delegate="doSomething($event)" style="border-radius:0px"/>
          </div>
          <div class="control">
            <!--initializing ProgressBar control-->
            <div id="progressBar" ej-progress-bar="e-value.bind:value;e-height.bind:height;" e-on-create.trigger="create()"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

{% endhighlight %}

* Create `progressbar.js` file inside `src/samples/progressbar` folder with below code snippet.

It also includes a Password field and through that the progress of the **ProgressBar** can be controlled

Initialize **ProgressBar** in script.

{% highlight js %}
export class DefaultFunctionalities {
constructor() {
this.value = 45;
this.height = '20';
}

create() {
$("#progressBar").ejProgressBar({
height: 20,
value: 30,  
width: 200,
});
progresObj = $("#progressBar").data("ejProgressBar");
progresObj.option("text", "weak");
$(".e-progress").css({ "background-color": "#DE0909", "border-radius": "10px" });
$(".e-progressbar").css({ "border-radius": "10px", "border": "1px solid black" });
} 
}

{% endhighlight %}

Here, you can initialize the properties of the **ProgressBar** such as height, value, width, text that is applied to the control by default.

The following screenshot displays a **ProgressBar** control.

![](/js/ProgressBar/Getting-Started_images/Getting-Started_img2.png) 

Include the following code within the **&lt;head&gt;** tag to change the page layout.

{% highlight css %}

   /*applying styles */
   .frame {
       border: 1px solid #BBBCBB;
       border-radius: 10px 10px 10px 10px;
       padding: 50px 60px;
       margin-top: 40px;
       width: 400px;
       margin-left: 400px;
   }
   .control {
       margin-bottom: 5px;
       margin-left: 230px;
   }
   .wrap_up {
       margin-left: 105px;
       font-size: 18px;
   }
   #progressBar {
       margin-top: 10px;
   } 

{% endhighlight %}

## Progress Control using Length of the Password Field

In real-time scenario, the progress of **ProgressBar** is changed according to the length of text in the password field by binding the change in the properties of control and checking the length of the password field.

Add the following code example inside the **&lt;script&gt;** tag of your **HTML** file.

{% highlight js %}

let progresObj, buttonObj, k = 10, timer = window.clearInterval(timer), i = 0, obj;
export class DefaultFunctionalities {
constructor() {
this.value = 45;
this.height = '20';
}

create() {
$("#progressBar").ejProgressBar({
height: 20,
value: 30,  /*Specify the initial value of the progress in percentage*/
width: 200,
});
}
doSomething($event) {
progresObj = $("#progressBar").data("ejProgressBar");
i = $("#password").val().length;
if (i < 5) 
            this.weak();
        else if (i > 5 && i < 7) 
            this.Strong();
        else if(i>7) 
        var pwd = $("#password").val();
        if(/^[a-zA-Z0-9- ]*$/.test(pwd) == false);
            this.very_strong();
    }
     Strong() {  	 //Change the width and text of the progress ... called when the length is greater than 5
        progresObj.option("text", "strong");
        progresObj.option("percentage", k + 50);
        $(".e-progress").css("background-color", "#0055FF");
        $(".e-progressbar").css("color", "#000000");       
    }
     very_strong() {   //Change the width and text of the progress ... called when the length is greater than 7
        progresObj.option("text", "Very strong");
        progresObj.option("percentage", k + 90);
        $(".e-progress").css("background-color", "Green");
        $(".e-progressbar").css("color", "#000000");   
    }
     weak() {   //Change the width and text of the progress... called when the length is less than 5
        progresObj.option("text", "Weak");
        progresObj.option("percentage", k+20 );
        $(".e-progress").css("background-color", "#DE0909");
        $(".e-progressbar").css("border-radius", "10px");      
    }
}

{% endhighlight %}

You can calculate length of the password and call the appropriate function that changes the percentage property of **ProgressBar**.

* The **weak()** function changes the text inside the ProgressBar to **Weak** and percentage to 30, that is invoked when the length of the text is less than 5.
* The **strong()** function changes the text inside the ProgressBar to **Strong** and percentage to 60, that is invoked when the length of the text exceeds 5.
* The **very_strong()** function changes the text inside the ProgressBar to Very **Strong** and percentage to 100, that is invoked when the length of the text exceeds 7 and the text contains a symbol in it.

You can change themes or appearance of the ProgressBar as required.

The final output is displayed as follows.

![](/js/ProgressBar/Getting-Started_images/Getting-Started_img3.png) 

![](/js/ProgressBar/Getting-Started_images/Getting-Started_img4.png) 

![](/js/ProgressBar/Getting-Started_images/Getting-Started_img5.png) 

You can also bind an event at the start and finish of a ProgressBar by using the start, complete and change properties of the ProgressBar.

