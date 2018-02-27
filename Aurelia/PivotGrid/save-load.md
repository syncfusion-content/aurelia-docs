---
layout: post
title: Save and Load Report
description: save and load report
platform: js
control: PivotGrid
documentation: ug
api: /api/js/ejpivotgrid
---

# Save and Load Report

Allows you to save the current report of PivotGrid and render the control with the saved report later.

## Save report to local storage

You can save the current report of PivotGrid to the local storage by calling the [`saveReport`](/api/js/ejpivotgrid#members:saveReport) method of the PivotGrid.

{% highlight html %}

<template>
   <div>
   <ej-pivot-grid id="PivotGrid1" e-on-save-report.delegate="saveToLocal($event.detail)">
    </ej-pivot-grid>
    </div>
    <button id="button" ej-button="e-text.bind:textValue1" e-on-click.trigger="saveLocal($event)" style="margin-top: 10px">Save</button>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {

 saveLocal(args) {
          let pGridObj = $('.e-pivotgrid').data("ejPivotGrid");
          url = "",
          name = "report",
          storage = "local",
          pGridObj.saveReport(name, storage, url);
    }

 saveToLocal(args) {
    localStorage.setItem("report", JSON.stringify(args.report));
    }
}

{% endhighlight %}

## Load report from local storage

To load the stored report of PivotGrid from the local storage, you should call the ['loadReport'](/api/js/ejpivotgrid#members:loadReport) method in the PivotGrid.

{% highlight html %}

<template>
   <div>
   <ej-pivot-grid id="PivotGrid1" e-on-load-report.delegate="loadFromLocal($event.detail)">
    </ej-pivot-grid>
    </div>
    <button id="button" ej-button="e-text.bind:textValue1" e-on-click.trigger="loadReport($event)" style="margin-top: 10px">Load</button>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {

  loadReport(args) {
            let pGridObj = $('.e-pivotgrid').data("ejPivotGrid");
            url = "",
            name = "report",
            storage = "local",
            pGridObj.loadReport(name, storage, url);
    }
  loadFromLocal(args){
      args.targetControl.model.dataSource = JSON.parse(localStorage.getItem("report"));
   }
}

{% endhighlight %}
