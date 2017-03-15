---
layout: post
title:  Responsive
description: Responsive
documentation: ug
platform: Aurelia
keywords: responsive,kanban responsive
---

# Responsive

The Kanban control has support for responsive behavior based on client browser’s width and height. To enable responsive, [`e-is-responsive`](https://help.syncfusion.com/api/js/ejkanban#members:isresponsive) property should be true.There are two modes of responsive layout is available in Kanban based on client width. They are.

* Mobile(<480px)
* Desktop(>480px)

You can check the image representation of touch actions from the below image.

![](Responsive_images/KanbanOverlayImage.png)

## Width

By default, the Kanban is adaptable to its parent container. It can adjust its width of columns based on parent container width. You can also assign width of [`ej-kanban-column`](https://help.syncfusion.com/api/js/ejkanban#members:columns) in percentage. 

The following code example describes the above behavior.


{% highlight html %}

<template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData" e-is-responsive="true" e-key-field="Status" e-fields.bind="Field">
            <ej-kanban-column e-header-text="Backlog" e-key="Open" e-width=10%></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress" e-key="InProgress" e-width=10%></ej-kanban-column>
            <ej-kanban-column e-header-text="Done" e-key="Close" e-width=10%></ej-kanban-column>
        </ej-kanban>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Kanban {
    constructor() {
        this.KanbanData = [
           { Id: 1, Status: "Open", Summary: "Analyze the new requirements gathered from the customer.", Type: "Story", Priority: "Low", Tags: "Analyze,Customer", Estimate: 3.5, Assignee: "Nancy Davloio", ImgUrl: "/images/kanban/1.png", RankId: 1 },
           { Id: 2, Status: "InProgress", Summary: "Improve application performance", Type: "Improvement", Priority: "Normal", Tags: "Improvement", Estimate: 6, Assignee: "Andrew Fuller", ImgUrl: "/images/kanban/2.png", RankId: 1 },
           { Id: 3, Status: "Open", Summary: "Arrange a web meeting with the customer to get new requirements.", Type: "Others", Priority: "Critical", Tags: "Meeting", Estimate: 5.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 2 },
           { Id: 4, Status: "InProgress", Summary: "Fix the issues reported in the IE browser.", Type: "Bug", Priority: "Release Breaker", Tags: "IE", Estimate: 2.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 2 },
           { Id: 5, Status: "Testing", Summary: "Fix the issues reported by the customer.", Type: "Bug", Priority: "Low", Tags: "Customer", Estimate: "3.5", Assignee: "Steven walker", ImgUrl:"/images/kanban/5.png", RankId: 1 },
           { Id: 6, Status: "Close", Summary: "Arrange a web meeting with the customer to get the login page requirements.", Type: "Others", Priority: "Low", Tags: "Meeting", Estimate: 2, Assignee: "Michael Suyama", ImgUrl: "/images/kanban/6.png", RankId: 1 },
           { Id: 7, Status: "Validate", Summary: "Validate new requirements", Type: "Improvement", Priority: "Low", Tags: "Validation", Estimate: 1.5, Assignee: "Robert King", ImgUrl: "/images/kanban/7.png", RankId: 1 },
           { Id: 8, Status: "Close", Summary: "Login page validation", Type: "Story", Priority: "Release Breaker", Tags: "Validation,Fix", Estimate: 2.5, Assignee: "Laura Callahan", ImgUrl: "/images/kanban/8.png", RankId: 2 },
           { Id: 9, Status: "Testing", Summary: "Fix the issues reported in Safari browser.", Type: "Bug", Priority: "Release Breaker", Tags: "Fix,Safari", Estimate: 1.5, Assignee: "Nancy Davloio", ImgUrl: "/images/kanban/1.png", RankId: 2 },
           { Id: 10, Status: "Close", Summary: "Test the application in the IE browser.", Type: "Story", Priority: "Low", Tags: "Testing,IE", Estimate: 5.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 3 },
           { Id: 11, Status: "Validate", Summary: "Validate the issues reported by the customer.", Type: "Story", Priority: "High", Tags: "Validation,Fix", Estimate: 1, Assignee: "Steven walker", ImgUrl: "/images/kanban/5.png", RankId: 1 },
           { Id: 12, Status: "Testing", Summary: "Check Login page validation.", Type: "Story", Priority: "Release Breaker", Tags: "Testing", Estimate: 0.5, Assignee: "Michael Suyama", ImgUrl: "/images/kanban/6.png", RankId: 3 },
           { Id: 13, Status: "Open", Summary: "API improvements.", Type: "Improvement", Priority: "High", Tags: "Grid,API", Estimate: 3.5, Assignee: "Robert King", ImgUrl: "/images/kanban/7.png", RankId: 3 },
           { Id: 14, Status: "InProgress", Summary: "Add responsive support to application", Type: "Epic", Priority: "Critical", Tags: "Responsive", Estimate: 6, Assignee: "Laura Callahan", ImgUrl: "/images/kanban/8.png", RankId: 3 },
           { Id: 15, Status: "Open", Summary: "Show the retrieved data from the server in grid control.", Type: "Story", Priority: "High", Tags: "Database,SQL", Estimate: 5.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 4 },
           { Id: 16, Status: "InProgress", Summary: "Fix cannot open user’s default database SQL error.", Priority: "Critical", Type: "Bug", Tags: "Database,Sql2008", Estimate: 2.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 4 },
           { Id: 17, Status: "Testing", Summary: "Fix the issues reported in data binding.", Type: "Story", Priority: "Normal", Tags: "Databinding", Estimate: "3.5", Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 4 },
           { Id: 18, Status: "Close", Summary: "Analyze SQL server 2008 connection.", Type: "Story", Priority: "Release Breaker", Tags: "Grid,Sql", Estimate: 2, Assignee: "Andrew Fuller", ImgUrl: "/images/kanban/2.png", RankId: 4 },
           { Id: 19, Status: "Validate", Summary: "Validate databinding issues.", Type: "Story", Priority: "Low", Tags: "Validation", Estimate: 1.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 1 },
           { Id: 20, Status: "Close", Summary: "Analyze grid control.", Type: "Story", Priority: "High", Tags: "Analyze", Estimate: 2.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 5 }];
        this.Field = { primaryKey: 'Id', content: 'Summary', tag: 'Tags'};
    }
}

{% endhighlight %}

N> `e-allow-scrolling` should be false while defining width in percentage.

## Min Width

Min Width is used to maintain minimum width for the Kanban. If the Kanban width is less than [`e-min-width`](https://help.syncfusion.com/api/js/ejkanban#members:minwidth) then the scrollbar will be displayed to maintain minimum width.

The following code example describes the above behavior.


{% highlight html %}

<template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData" e-is-responsive="true" e-min-width=700 e-key-field="Status" e-fields.bind="Field">
            <ej-kanban-column e-header-text="Backlog" e-key="Open" e-width=120></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress" e-key="InProgress" e-width=110></ej-kanban-column>
            <ej-kanban-column e-header-text="Done" e-key="Close" e-width=></ej-kanban-column>
        </ej-kanban>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Kanban {
    constructor() {
        this.KanbanData = [
           { Id: 1, Status: "Open", Summary: "Analyze the new requirements gathered from the customer.", Type: "Story", Priority: "Low", Tags: "Analyze,Customer", Estimate: 3.5, Assignee: "Nancy Davloio", ImgUrl: "/images/kanban/1.png", RankId: 1 },
           { Id: 2, Status: "InProgress", Summary: "Improve application performance", Type: "Improvement", Priority: "Normal", Tags: "Improvement", Estimate: 6, Assignee: "Andrew Fuller", ImgUrl: "/images/kanban/2.png", RankId: 1 },
           { Id: 3, Status: "Open", Summary: "Arrange a web meeting with the customer to get new requirements.", Type: "Others", Priority: "Critical", Tags: "Meeting", Estimate: 5.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 2 },
           { Id: 4, Status: "InProgress", Summary: "Fix the issues reported in the IE browser.", Type: "Bug", Priority: "Release Breaker", Tags: "IE", Estimate: 2.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 2 },
           { Id: 5, Status: "Testing", Summary: "Fix the issues reported by the customer.", Type: "Bug", Priority: "Low", Tags: "Customer", Estimate: "3.5", Assignee: "Steven walker", ImgUrl:"/images/kanban/5.png", RankId: 1 },
           { Id: 6, Status: "Close", Summary: "Arrange a web meeting with the customer to get the login page requirements.", Type: "Others", Priority: "Low", Tags: "Meeting", Estimate: 2, Assignee: "Michael Suyama", ImgUrl: "/images/kanban/6.png", RankId: 1 },
           { Id: 7, Status: "Validate", Summary: "Validate new requirements", Type: "Improvement", Priority: "Low", Tags: "Validation", Estimate: 1.5, Assignee: "Robert King", ImgUrl: "/images/kanban/7.png", RankId: 1 },
           { Id: 8, Status: "Close", Summary: "Login page validation", Type: "Story", Priority: "Release Breaker", Tags: "Validation,Fix", Estimate: 2.5, Assignee: "Laura Callahan", ImgUrl: "/images/kanban/8.png", RankId: 2 },
           { Id: 9, Status: "Testing", Summary: "Fix the issues reported in Safari browser.", Type: "Bug", Priority: "Release Breaker", Tags: "Fix,Safari", Estimate: 1.5, Assignee: "Nancy Davloio", ImgUrl: "/images/kanban/1.png", RankId: 2 },
           { Id: 10, Status: "Close", Summary: "Test the application in the IE browser.", Type: "Story", Priority: "Low", Tags: "Testing,IE", Estimate: 5.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 3 },
           { Id: 11, Status: "Validate", Summary: "Validate the issues reported by the customer.", Type: "Story", Priority: "High", Tags: "Validation,Fix", Estimate: 1, Assignee: "Steven walker", ImgUrl: "/images/kanban/5.png", RankId: 1 },
           { Id: 12, Status: "Testing", Summary: "Check Login page validation.", Type: "Story", Priority: "Release Breaker", Tags: "Testing", Estimate: 0.5, Assignee: "Michael Suyama", ImgUrl: "/images/kanban/6.png", RankId: 3 },
           { Id: 13, Status: "Open", Summary: "API improvements.", Type: "Improvement", Priority: "High", Tags: "Grid,API", Estimate: 3.5, Assignee: "Robert King", ImgUrl: "/images/kanban/7.png", RankId: 3 },
           { Id: 14, Status: "InProgress", Summary: "Add responsive support to application", Type: "Epic", Priority: "Critical", Tags: "Responsive", Estimate: 6, Assignee: "Laura Callahan", ImgUrl: "/images/kanban/8.png", RankId: 3 },
           { Id: 15, Status: "Open", Summary: "Show the retrieved data from the server in grid control.", Type: "Story", Priority: "High", Tags: "Database,SQL", Estimate: 5.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 4 },
           { Id: 16, Status: "InProgress", Summary: "Fix cannot open user’s default database SQL error.", Priority: "Critical", Type: "Bug", Tags: "Database,Sql2008", Estimate: 2.5, Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 4 },
           { Id: 17, Status: "Testing", Summary: "Fix the issues reported in data binding.", Type: "Story", Priority: "Normal", Tags: "Databinding", Estimate: "3.5", Assignee: "Janet Leverling", ImgUrl: "/images/kanban/3.png", RankId: 4 },
           { Id: 18, Status: "Close", Summary: "Analyze SQL server 2008 connection.", Type: "Story", Priority: "Release Breaker", Tags: "Grid,Sql", Estimate: 2, Assignee: "Andrew Fuller", ImgUrl: "/images/kanban/2.png", RankId: 4 },
           { Id: 19, Status: "Validate", Summary: "Validate databinding issues.", Type: "Story", Priority: "Low", Tags: "Validation", Estimate: 1.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 1 },
           { Id: 20, Status: "Close", Summary: "Analyze grid control.", Type: "Story", Priority: "High", Tags: "Analyze", Estimate: 2.5, Assignee: "Margaret hamilt", ImgUrl: "/images/kanban/4.png", RankId: 5 }];
        this.Field = { primaryKey: 'Id', content: 'Summary', tag: 'Tags'};
    }
}

{% endhighlight %}

The following output is displayed as a result of the above code example.

![](Responsive_images/responsive_img1.png)
