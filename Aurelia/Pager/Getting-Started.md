---
layout: post
title: getting-started | Pager | Aurelia | Syncfusion
description: getting started for Pager
platform: aurelia
control: Pager
documentation: ug
---

# Getting Started

This section discloses the details on how to render and configure Pager component in an Aurelia application.

## Create Pager

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).
We have already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight javascript %}

*	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 
*	cd syncfusion-template-repository
*	npm install
*	jspm install

{% endhighlight %}

The below steps describes the steps to create Syncfusion Aurelia Pager component.

The **Essential Javascript Aurelia Pager** control render's based on total records count, page size, page count values.

Create `pager` folder inside `src/samples/` location in sample files folder.

Create an HTML file (here `pager.html` file) inside newly created folder and use the below code example to render the Pager component.

{% highlight HTML %}

<ej-pager e-total-records-count.bind=totalRecordsCount id="pager"></ej-pager>

{% endhighlight %}

N> The `totalRecordsCount, pageSize` and `pageCount` API values play a key role in rendering a pager control. Since `pageSize` and `pageCount` API's are dependent on each other and pager will be updated each time the value changes as explained below.

**Total records Count:** totalRecordsCount defines the total number of records which is bounded as a single data.

Create a javascript file in Aurelia application and add the Model class for binding with Pager component as given below.
Here, for example, we created the  `pager.js` file with the below code snippet inside `src/samples/pager` folder.

{% highlight javascript %}

export class Pager{
      constructor() {
      this.totalRecordsCount = 20;
    }
}

{% endhighlight %}

### Configure Router

Now that, we are done with adding Pager component, let us see how to configure our Aurelia application to add additional tab for showcasing Pager component.

The Routing configuration is available inside 'src/app.js' file.

Add the below  code to the config.map method.

{% highlight javascript %}

{ route: 'pager', name: 'pager', moduleId: 'samples/pager/pager', nav: true, title: 'Pager' }

{% endhighlight %}

### Run the application

Execute the following command to run the application

{% highlight javascript %}

gulp watch

{% endhighlight %}

Execution of above code will render the following output.

![Pager](Getting-Started_images/Getting-Started_img1.png)

**Page Size:**  pageSize value defines the number of records to be displayed per page. The default value for the pageSize API is 12.

{% highlight HTML %}

<ej-pager e-page-size.bind=size e-total-records-count.bind=totalRecordsCount id="pager"></ej-pager>

{% endhighlight %}

{% highlight javascript %}

export class Pager{
    constructor() {
      this.size = 1;
      this.totalRecordsCount = 20;
    }
}

{% endhighlight %}

Run the above sample to get the below output.

![Page Size](Getting-Started_images/Getting-Started_img2.png)

**Page Count:**  pageCount value defines the number of pages to be displayed in the pager control for navigation. The default value for pageCount is 10 and value will be updated based on `totalRecordsCount` and pageSize values.

{% highlight HTML %}

<ej-pager e-page-size.bind=size e-total-records-count.bind=totalRecordsCount e-page-count.bind=pageCount id="pager"></ej-pager>

{% endhighlight %}

{% highlight javascript %}

export class Pager{
    constructor() {
      this.size = 1;
      this.totalRecordsCount = 20;
      this.pageCount = 3;
    }
}

{% endhighlight %}

Run the above sample to get the below output.

![Page Count](Getting-Started_images/Getting-Started_img3.png)
