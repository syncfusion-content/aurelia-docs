---
title: Export
description: export
platform: Aurelia
control: PivotChart
documentation: ug
api: /api/js/ejpivotchart
---

# Exporting

The pivot chart control can be exported to the following file formats:

* Microsoft Excel
* Microsoft Word
* PDF
* Image

The pivot chart control can be exported by invoking the `exportPivotChart` method with an appropriate export option as parameter.

{% highlight html %}

<template>
  <div>
  <div>
    <ej-pivot-chart e-data-source.bind="pivotData" e-load.bind="loadTheme" e-common-series-options.bind="commonSeries" e-legend.bind="legend"
      e-size.bind="size" e-primary-y-axis.bind="primaryYAxis">
    </ej-pivot-chart>
    </div>
    <div>Exporting:</div>
    <button id="button" ej-button="e-text.bind:textValue1" e-on-click.trigger="exportBtnClick($event)" style="margin-top: 10px">Apply</button>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {
  constructor() {

        ... //datasource
    }

    exportBtnClick() {
    let chartObj = $('.e-pivotchart').data('ejPivotChart');
    chartObj.exportPivotChart("https://js.syncfusion.com/ejservices/api/PivotChart/Olap/ExcelExport","fileName");
   }
}

{% endhighlight %}

## Excel export

You can export the contents of the pivot chart to an Excel document for future archival, references, and analysis purposes.

{% highlight javascript %}

export class BasicUse {
  constructor() {

        ... //datasource
    }

    exportBtnClick() {
    let chartObj = $('.e-pivotchart').data('ejPivotChart');
    chartObj.exportPivotChart("https://js.syncfusion.com/ejservices/api/PivotChart/Olap/ExcelExport","fileName");
   }
}

{% endhighlight %}

## Word export

You can export the contents of the pivot chart to a Word document for future archival, references, and analysis purposes.

{% highlight javascript %}

export class BasicUse {

    exportBtnClick() {
    let chartObj = $('.e-pivotchart').data('ejPivotChart');
    chartObj.exportPivotChart("https://js.syncfusion.com/ejservices/api/PivotChart/Olap/WordExport","fileName");
   }
}

{% endhighlight %}

## PDF export

You can export the contents of the pivot chart to PDF document for future archival, references, and analysis purposes.

{% highlight javascript %}

export class BasicUse {

    exportBtnClick() {
    let chartObj = $('.e-pivotchart').data('ejPivotChart');
    chartObj.exportPivotChart("https://js.syncfusion.com/ejservices/api/PivotChart/Olap/PDFExport","fileName");
   }
}

{% endhighlight %}

## Image export

You can export the contents of the pivot chart to image format for future archival, references, and analysis purposes. You can export the pivot chart to the following image formats:

* PNG
* EMF
* JPG
* GIF
* BMP

To export the pivot chart in PNG format, the service URL, the file name, and the **“ej.PivotChart.ExportOptions.PNG”** enumeration value are set as parameters. It is similar to other image formats.

{% highlight javascript %}

export class BasicUse {

  exportBtnClick() {
    let chartObj = $('.e-pivotchart').data('ejPivotChart');
    chartObj.exportPivotChart("https://js.syncfusion.com/ejservices/api/PivotChart/Olap/ImageExport","fileName", ej.PivotChart.ExportOptions.PNG);
   }
}

{% endhighlight %}

## Pivot chart - exporting format

I> This option is applicable only for the pivot chart specifically when it is exported to an Excel document.

You can set an option to export the pivot chart to an Excel document, and you can export it as either an image or pivot chart format itself by setting the Boolean property `exportChartAsImage` in the `beforeExport` event.

N> By default, the pivot chart will be exported in image format to an Excel document.

{% highlight html %}

<template>
  <div>
    <ej-pivot-chart  e-on-before-exporting.delegate="Exporting($event.detail)">
    </ej-pivot-chart>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {

    Exporting(e) {
        e.exportChartAsImage = true;
   }
}

{% endhighlight %}

## Exporting customization

You can add the title and description to the exporting document by using the title and description property in the "beforeExport" event.

N> The title and description cannot be added to image formats.

{% highlight html %}

<template>
   <div>
   <ej-pivot-chart id="PivotChart1" e-on-before-export.delegate="Exporting($event.detail)">
    </ej-pivot-chart>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {

    Exporting(args) {
        args.title = "PivotChart";
        args.description = "Visualizes both OLAP and Relational datasource in graphical format";
    }
}

{% endhighlight %}
