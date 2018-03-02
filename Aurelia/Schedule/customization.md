---
title: Schedule - Customization	
description: Customization of working hours, date, and appointment window
platform: Aurelia
control: schedule
documentation: ug
keywords: customization, work hours, appointment window, display hours, Query cell info
---
# Customization

The Scheduler can be customized in various aspects like -

* Setting different Start/end hour limits
* Highlighting the working hours
* Setting different [date format](/aurelia/schedule/globalization-and-localization#date-format)
* Specifying minimum and maximum date ranges
* Customize the entire appointment window with the user required fields
* Setting different time Slot duration
* Complete Scheduler customization using queryCellInfo event
* Setting different [first day of week](/aurelia/schedule/globalization-and-localization#first-day-of-week)

## Hour Customization

It includes customization of displaying Scheduler with specific Start/End hours and also defining the working hour time range which is differentiated as business hours.

### Schedule Display Hours

It denotes the start and end hour time limits to be displayed on the Scheduler. To set this time limit, two properties namely [startHour](/api/js/ejschedule#members:starthour) and [endHour](/api/js/ejschedule#members:endhour) can be used.

* **startHour** - The hour from which the Scheduler time display actually starts.
* **endHour** - The hour on which the Scheduler time display should end.

The following code example renders the scheduler from 7.00 AM to 6.00 PM.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-width="100%" e-start-hour="7" e-end-hour="18" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            dataSource: [{
                Id: 101,
                Subject: "Talk with Nature",
                StartTime: new Date(2015, 11, 5, 10, 00),
                EndTime: new Date(2015, 11, 5, 11, 00)
            }]
        };
    }
}

{% endhighlight %}

### Working Hours

Working hours indicates the work hour limit within the Scheduler, which is highlighted visually with white colored work cells. To enable the highlighting of work hours on the Scheduler, set the **highlight** option available within the workHours property to **true**. By default, it is set to true. [workHour](/api/js/ejschedule#members:workhours) is a object property which contains the below specified options,

* **[highlight](/api/js/ejschedule#members:workhours-highlight)** – enables/disables the highlighting of work hours.
* **[start](/api/js/ejschedule#members:workhours-start)** - sets the start time of the working/business hour in a day.
* **[end](/api/js/ejschedule#members:workhours-end)** - sets the end time limit of the working/business hour in a day.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-width="100%" e-work-hours.bind="WorkHourSettings" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.WorkHourSettings = {
            highlight: true,
            start: 8,
            end: 16
        };
        this.AppointmentList = {
            dataSource: [{
                Id: 101,
                Subject: "Talk with Nature",
                StartTime: new Date(2015, 11, 5, 10, 00),
                EndTime: new Date(2015, 11, 5, 11, 00)
            }]
        };
    }
}

{% endhighlight %}

N> By default, work hour **start** is set to **9** and **end** is set to **18**. Also, the Scheduler cells automatically scrolls up or down based on the starting work hour, to make the user to view that particular time initially.

## TimeScale

The [TimeScale](/api/js/ejschedule#members:timeScale) allows the user to set the required time slot duration for the work cells that displays on the Scheduler. It provides option to customize both the major and minor slots using template option. It includes the below properties such as,

* [enable](/api/js/ejschedule#members:timeScale-enable) - It accepts true or false value, denoting whether to show or hide the time slots. Its default value is `true`.
* [majorSlot](/api/js/ejschedule#members:timeScale-majorSlot) – Specifies the major time slot duration.
* [minorSlotCount](/api/js/ejschedule#members:timeScale-minorSlotCount) – Specifies the value, based on which the minor time slots are divided into appropriate count.
* [TimeScale templates](/aurelia/schedule/templates#timescale-templates) - 2 template options available for customizing timeScales namely `minorSlotTemplateId` and `majorSlotTemplateId`.

The majorSlot and minorSlot can be set on the Scheduler with the following code example.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-width="100%" e-time-scale.bind="TimeScaleSettings" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.TimeScaleSettings = {
            enable: true,
            majorSlot: 60,
            minorSlotCount: 6
        };
        this.AppointmentList = {
            dataSource: [{
                Id: 100,
                Subject: "Wild Discovery",
                StartTime: new Date(2015, 11, 2, 9, 00),
                EndTime: new Date(2015, 11, 2, 10, 30),
                Location: "CHINA"
            }]
        };
    }
}

{% endhighlight %}

## Hide Weekend days

The Scheduler can be customized to display only the working days, thus hiding the weekend days from it. The working days render based on the values given in the [workWeek](/api/js/ejschedule#members:workweek) property. The days that are not mentioned in the `workWeek` collection is considered to be the weekend days and it can be hidden from the Scheduler by setting `false` to the [showWeekend](/api/js/ejschedule#members:showweekend) property.

The following code example renders the Scheduler by hiding the weekend days.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-width="100%" e-show-weekend="false" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            dataSource: [{
                Id: 101,
                Subject: "Talk with Nature",
                StartTime: new Date(2015, 11, 5, 10, 00),
                EndTime: new Date(2015, 11, 5, 11, 00)
            }]
        };
    }
}

{% endhighlight %}

## Date Customization

The date in the Scheduler can be customized by setting specific minimum and maximum date ranges and also defining various date formats to it.

### Current Date

The Current date indicates the date with which the Scheduler loads initially and based on which the appropriate date range displays in the week/workweek/month/agenda views. To set the current date to the Scheduler – use the following code example,

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/05/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            dataSource: [{
                Id: 101,
                Subject: "Talk with Nature",
                StartTime: new Date(2015, 11, 5, 10, 00),
                EndTime: new Date(2015, 11, 5, 11, 00)
            }]
        };
    }
}

{% endhighlight %}

N> By default, the System current date will be taken as Scheduler’s current date.

### MinDate and MaxDate

Providing the [minDate](/api/js/ejschedule#members:mindate) and [maxDate](/api/js/ejschedule#members:maxdate) property with some date values, allows the Scheduler to set the minimum and maximum date range. The Scheduler date that lies beyond these minimum and maximum date range will be in a disabled state, so that the date navigation is blocked beyond these specified date range. Also, the appointments that lies beyond these date ranges will not be displayed on the Scheduler.

The following code example shows how to set the minDate and maxDate properties of the Scheduler.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/05/2015" e-min-date="11/04/2015" e-max-date="11/08/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            dataSource: [{
                Id: 101,
                Subject: "Talk with Nature",
                StartTime: new Date(2015, 11, 5, 10, 00),
                EndTime: new Date(2015, 11, 5, 11, 00)
            }]
        };
    }
}

{% endhighlight %}

N> The **maxDate** value provided should always be greater than that of **minDate** value.

## Appointment Window Customization

It is possible to use the custom appointment window option to design it with the user-required extra fields apart from the other default available fields. To make use of the customized appointment window, it is necessary to use the [appointmentWindowOpen](/api/js/ejschedule#events:appointmentwindowopen) event within which the display of default appointment window is prevented.

The following code example lets you create the custom appointment window (using recurrence editor feature) with a single extra field for defining the appointment type.

{% highlight html %}

<template>
    <require from="./custom-window.css"></require>
    <div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="575px" e-appointment-settings.bind="AppointmentList" e-current-date="06/05/2017"
            e-on-appointment-window-open.trigger="onAppointmentWindowOpen($event)" e-on-cell-click.trigger="onClick($event)"
            e-on-create.trigger="onCreate($event)">
        </ej-schedule>
    </div>
    <div class="cwindow">
        <ej-dialog id="customWindow" e-width="600px" e-target=".cwindow" e-height="auto" e-show-on-init="false" e-enable-model="true" e-title="Create Appointment"
                   e-css-class="e-scheduledialog" e-enable-resize="false" e-allow-keyboard-navigation="false" e-on-close.trigger="clearFields($event)">
            <div id="appointmentWindow" class="appointmentWindow">
                <form id="customAppointmentWindow">
                    <table width="100%" cellpadding="5">
                        <tbody>
                            <tr id="customId" style="display: none">
                                <td><label>Id:</label></td>
                                <td colspan="4">
                                    <input id="Id" class="Id" type="text" name="Id" />
                                </td>
                            </tr>
                            <tr id="customSubject">
                                <td class="e-textlabel">Subject:</td>
                                <td colspan="4">
                                    <input id="Subject" class="Subject" type="text" value="" name="Subject" style="width: 100%" />
                                </td>
                            </tr>
                            <tr id="customDescription">
                                <td class="e-textlabel">Description:</td>
                                <td colspan="4">
                                    <textarea id="Description" class="Description" name="Description" rows="3" cols="50" style="width: 100%; height: 60px !important; resize: vertical"></textarea>
                                </td>
                            </tr>
                            <tr id="customStartendtime">
                                <td class="e-textlabel">StartTime:</td>
                                <td colspan="2">
                                    <input id="StartTime" class="StartTime" type="text" value="" name="StartTime" />
                                </td>
                                <td class="e-textlabel">EndTime:</td>
                                <td colspan="2">
                                    <input id="EndTime" class="EndTime" type="text" value="" name="EndTime" />
                                </td>
                            </tr>
                            <tr id="customAlldayrecurcheck">
                                <td colspan="4">
                                    <div id="allDayCheck" class="customAlign">
                                        <div class='e-textlabel customAlign'>AllDay:</div>
                                        <div class="customAlign">
                                            <input ej-check-box="e-checked.two-way:allDay" e-on-change.trigger="onCheckboxChange($event)" id="AllDay" />
                                        </div>
                                    </div>
                                    <div id="recurCheck" class="customAlign">
                                        <div class="e-textlabel customAlign">Recurrence:</div>
                                        <div class="customAlign">
                                            <input ej-check-box="e-checked.two-way:recurrence" e-on-change.trigger="onCheckboxChange($event)" id="Recurrence" />
                                        </div>
                                    </div>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </form>
                <div id="buttonAction" style="position:relative;height:40px;">
                    <div style="width:220px;position:absolute;right:0px;">
                        <button ej-button="" id="appcancel" class="e-appButton e-appCancel" e-on-click.trigger="onButtonClick($event)" style="float: right; margin-bottom: 10px;">Cancel</button>
                        <button ej-button="" id="appsubmit" class="e-appButton e-appOk" e-on-click.trigger="onButtonClick($event)" style="float: right; margin-right: 10px; margin-bottom: 10px;">Submit</button>
                    </div>
                </div>
            </div>
            <div id="recurrenceWindow" class="recurrenceWindow" style="display:none;">
                <div id="customRecurrenceEditor"></div>
                <div id="buttonAction" style="position:relative;height:40px;">
                    <div style="width:220px;position:absolute;right:0px;">
                        <button ej-button="" id="recurcancel" class="e-recurButton e-recurCancel" e-on-click.trigger="onButtonClick($event)" style="float: right; margin-bottom: 10px;">Cancel</button>
                        <button ej-button="" id="recursubmit" class="e-recurButton e-recurOk" e-on-click.trigger="onButtonClick($event)" style="float: right; margin-right: 10px; margin-bottom: 10px;">Submit</button>
                    </div>
                </div>
            </div>
        </ej-dialog>
    </div>
</template>

{% endhighlight %}

The styles to be applied for the controls within the custom appointment window are as follows.

{% highlight css %}

<style type="text/css">
    #buttonAction {
        position: relative;
        height: 40px;
    }

    #buttonAction > div {
        width: 220px;
        position: absolute;
        right: 0px;
    }

    .validationError {
        background-color: #FF8A8A;
    }

    .customAlign {
        float: left;
        padding-right: 20px;
    }

    .e-scheduledialog table td {
        padding: 5px !important;
    }
</style>

{% endhighlight %}

Now, define the Schedule control with custom appointment window within script as shown below.

{% highlight javascript %}

export class CustomAppointmentWindow {
    onCreate(event) {
        let proxy = $('#Schedule1').ejSchedule('instance');
        proxy._customAppointmentWindow = $('#customWindow');
        proxy._customAppointmentWindow.ejDialog({ width: (proxy._mediaQuery) ? '100%' : 600, target: '#' + proxy._id, enableModal: true });
        proxy._customAppointmentWindow.parents().find('.e-scheduledialog').find('.e-titlebar').addClass('e-dialogheader');
        proxy._customAppointmentWindow.find('#StartTime,#EndTime').ejDateTimePicker({ width: '150px' });
        proxy._customAppointmentWindow.find('.e-appButton,.e-recurButton').ejButton({ width: '85px' });
        proxy._customAppointmentWindow.find('.AllDay,.Recurrence').ejCheckBox({ change: 'onCheckboxChange' });
        proxy._customAppointmentWindow.find('#customRecurrenceEditor').ejRecurrenceEditor({ frequencies: ['daily', 'weekly', 'monthly', 'yearly'], selectedRecurrenceType: 1 });
    }

    onClick(event) {
        let proxy = $('#Schedule1').ejSchedule('instance');
        let args = event.detail;
        proxy._customAllDay = $(args.target.currentTarget).closest('.e-alldaycells').hasClass('e-alldaycells');
    }

    onAppointmentWindowOpen(event) {
        let proxy = $('#Schedule1').ejSchedule('instance');
        let args = event.detail;
        args.cancel = true;
        proxy._customRecRule = null;
        if (!ej.isNullOrUndefined(args.appointment)) {
            proxy._customAppointmentWindow.find('#Id').val(args.appointment.Id);
            proxy._customAppointmentWindow.find('#Subject').val(args.appointment.Subject);
            proxy._customAppointmentWindow.find('#Description').val(args.appointment.Description);
            proxy._customAppointmentWindow.find('#StartTime').ejDateTimePicker({ value: new Date(args.appointment.StartTime) });
            proxy._customAppointmentWindow.find('#EndTime').ejDateTimePicker({ value: new Date(args.appointment.EndTime) });
            proxy._customAppointmentWindow.find('#AllDay').ejCheckBox({ checked: args.appointment.AllDay });
            proxy._customAppointmentWindow.find('#Recurrence').ejCheckBox({ checked: args.appointment.Recurrence });
            if (args.appointment.Recurrence) {
                if (proxy._currentAction == ej.Schedule.Actions.EditSeries) {
                    proxy._customRecRule = args.appointment.RecurrenceRule.split(';EXDATE')[0];
                } else if (proxy._currentAction == ej.Schedule.Actions.EditOccurrence) {
                    proxy._customAppointmentWindow.find('#Recurrence').ejCheckBox('disable');
                    proxy._customRecRule = args.appointment.RecurrenceRule;
                }
            }
        } else {
            proxy._customAppointmentWindow.find('#StartTime').ejDateTimePicker({ value: args.startTime });
            proxy._customAppointmentWindow.find('#EndTime').ejDateTimePicker({ value: args.endTime });
            if (!ej.isNullOrUndefined(args.target)) {
                if ($(args.target.currentTarget).closest('.e-alldaycells').hasClass('e-alldaycells') || proxy.currentView() == 'month' || proxy._customAllDay) {
                    proxy._customAppointmentWindow.find('#AllDay').ejCheckBox({ checked: true });
                    proxy._customAppointmentWindow.find('#StartTime,#EndTime').ejDateTimePicker({ enabled: false });
                }
            }
        }
        proxy._customAppointmentWindow.find('#appointmentWindow').css({ display: 'block' });
        proxy._customAppointmentWindow.find('#recurrenceWindow').css({ display: 'none' });
        proxy._customAppointmentWindow.ejDialog('open');
        let subject = proxy._customAppointmentWindow.find('#Subject');
        subject.focusin(function() { $(subject).removeClass('validationError'); }).focusout(function() { if ($(subject).val() == '') $(subject).addClass('validationError'); });
    }

    onButtonClick(event) {
        let proxy = $('#Schedule1').ejSchedule('instance');
        let args = event.detail;
        if ($(args.target).hasClass('e-appButton')) {
            if ($(args.target).hasClass('e-appOk')) {
                if (proxy._customAppointmentWindow.find('#Subject').val().trim() == '') return false;
                let appObj = {};
                let formElement = proxy._customAppointmentWindow.find('#customAppointmentWindow').get(0);
                for (let index = 0; index < formElement.length; index++) {
                    let columnName = formElement[index].name;
                    let $element = $(formElement[index]);
                    if (!ej.isNullOrUndefined(columnName) && columnName != '' && ej.isNullOrUndefined(appObj[columnName])) {
                        let value = formElement[index].value;
                        if (columnName == 'Id' && value != '') {
                            value = parseInt(string, value);
                        }
                        if ($element.hasClass('e-datetimepicker')) {
                            value = new Date(value);
                        }
                        if ($element.hasClass('e-checkbox')) {
                            value = formElement[index].checked;
                        }
                        if (columnName.indexOf('_hidden') == -1) {
                            appObj[columnName] = value;
                        }
                    }
                }
                if (appObj.Recurrence) {
                    appObj[proxy._appointmentSettings['recurrenceRule']] = proxy._customRecRule;
                    let recurEdit = proxy._appointmentAddWindow.find('.e-recurrenceeditor').data('ejRecurrenceEditor');
                    recurEdit._recRule = proxy._customRecRule;
                }
                proxy.saveAppointment(appObj);
            }
            proxy._customAppointmentWindow.ejDialog('close');
        } else {
            proxy._customAppointmentWindow.find('#appointmentWindow,#recurrenceWindow').toggle();
            if ($(args.target).hasClass('e-recurOk')) {
                let recurObj = proxy._customAppointmentWindow.find('#customRecurrenceEditor').ejRecurrenceEditor('instance');
                recurObj.closeRecurPublic();
                proxy._customRecRule = recurObj._recRule;
            } else {
                proxy._customAppointmentWindow.find('#Recurrence').ejCheckBox({ checked: false });
            }
        }
    }

    onCheckboxChange(event) {
        let proxy = $('#Schedule1').ejSchedule('instance');
        let args = event.detail;
        if (args.model.id == 'AllDay') {
            if (args.isChecked) {
                let startDate = new Date(proxy._customAppointmentWindow.find('#StartTime').ejDateTimePicker('model.value').setHours(0, 0, 0));
                let endDate = new Date(proxy._customAppointmentWindow.find('#EndTime').ejDateTimePicker('model.value').setHours(23, 59, 59));
                proxy._customAppointmentWindow.find('#StartTime').ejDateTimePicker({ value: new Date(startDate), enabled: false });
                proxy._customAppointmentWindow.find('#EndTime').ejDateTimePicker({ value: new Date(endDate), enabled: false });
            } else {
                proxy._customAppointmentWindow.find('#StartTime').ejDateTimePicker({ enabled: true });
                proxy._customAppointmentWindow.find('#EndTime').ejDateTimePicker({ enabled: true });
            }
        } else {
            if (args.isChecked) proxy._customAppointmentWindow.find('#appointmentWindow,#recurrenceWindow').toggle();
        }
    }

    clearFields() {
        let proxy = $('#Schedule1').ejSchedule('instance');
        proxy._customAppointmentWindow.find('#Id').val('');
        proxy._customAppointmentWindow.find('#Subject').val('');
        proxy._customAppointmentWindow.find('#Description').val('');
        proxy._customAppointmentWindow.find('#AllDay,#Recurrence').ejCheckBox({ checked: false });
        proxy._customAppointmentWindow.find('#AllDay,#Recurrence').ejCheckBox('enable');
        proxy._customAppointmentWindow.find('#StartTime,#EndTime').ejDateTimePicker({ enabled: true });
    }

    constructor() {
        this.recurrenceCheck = false;
        this.allDayCheck = false;
        this.Frequencies = ['daily', 'weekly', 'monthly', 'yearly'];
        this.AppointmentList = {
            dataSource: [{
                Id: 1,
                Subject: 'Brazil - Croatia',
                StartTime: '2017/6/2 09:00:00',
                EndTime: '2017/6/2 10:30:00',
                StartTimeZone: 'UTC +05:30',
                EndTimeZone: 'UTC +05:30',
                Description: '',
                AllDay: false,
                Recurrence: false
            }, {
                Id: 2,
                Subject: 'Mexico - Cameroon',
                StartTime: '2017/6/3 13:00:00',
                EndTime: '2017/6/3 14:30:00',
                StartTimeZone: 'UTC +05:30',
                EndTimeZone: 'UTC +05:30',
                Description: '',
                AllDay: false,
                Recurrence: false
            }],
            id: 'Id',
            subject: 'Subject',
            startTime: 'StartTime',
            endTime: 'EndTime',
            startTimeZone: 'StartTimeZone',
            endTimeZone: 'EndTimeZone',
            description: 'Description',
            allDay: 'AllDay',
            recurrence: 'Recurrence',
            recurrenceRule: 'RecurrenceRule'
        };
    }
}

{% endhighlight %}

## Scheduler Customization using queryCellInfo

It is possible to format and customize almost every child elements of scheduler such as work cells, header cells, time cells and so on using [queryCellInfo ](/api/js/ejschedule#events:appointmentwindowopen) event.

The following code snippet shows how to customize the appointment and work cells based on the query cell info event.

{% highlight html %}

<template>
    <require from="./cell-formatting.css"></require>
  <div>
      <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-current-date="06/05/2017" e-on-query-cell-info.trigger="checkInfo($event)"></ej-schedule>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    checkInfo(event) {
        let args = event.detail;
        switch (args.requestType) {
            case "workcells":
                args.element.css("background-color", "#ffe9cc");
                break;
            case "monthcells":
                args.element.css("background-color", "#faa41a");
                args.element.css("border-color", "#faa41a");
                break;
        }
    }
    constructor() { }
}

{% endhighlight %}

The Scheduler elements are listed below which can be formatted through this event. The names are listed in the format with which it can be accessed or used within the requestType argument of the event.

<table class="params">
    <thead>
        <tr>
            <th>Request Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">appointment</td>
            <td class="description">Depicts the appointment element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">agendacells</td>
            <td class="description">Depicts the Agenda Cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">alldaycells</td>
            <td class="description">Depicts the AllDay cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">headercells</td>
            <td class="description">Depicts the header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">resourceheadercells</td>
            <td class="description">Depicts the resource header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">leftheadercells</td>
            <td class="description">Depicts the left empty space on header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">leftindentcells</td>
            <td class="description">Depicts the left empty space on date cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">timecells</td>
            <td class="description">Depicts the left side time panel cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">headerdate</td>
            <td class="description">Depicts the header date cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">emptytd</td>
            <td class="description">Depicts the empty space above the vertical scroller within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">resourcegroupheader</td>
            <td class="description">Depicts the header group cell in horizontal orientation in the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">monthcells</td>
            <td class="description">Depicts the month cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">workcells</td>
            <td class="description">Depicts the work cell element within the Scheduler.</td>
        </tr>
    </tbody>
</table>
