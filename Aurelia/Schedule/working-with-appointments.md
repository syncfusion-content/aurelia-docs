---
title: Working with appointments
description: Working with Scheduler appointments and its related options like Recurrence.
platform: Aurelia
control: schedule
documentation: ug
keywords: appointments, recurrence, recurring appointment, resize, drag and drop, search, categorize, priority, occurrence, reminder, filter and CRUD
---

# Working with Appointments

An appointment represents a certain time interval in a schedule cell depicting a plan made for the specified time interval.

## Appointment Types

The types of appointments available within Scheduler can be categorized as follows

### Normal

Represents an appointment that is created for a certain time interval in one or more number of days. If the normal appointment is created for more than 24 hours, then those longer appointments will be rendered on the all-day row.

N> If the normal appointment is to be created for two days (say from November 25, 2015 – 11.00 PM to November 26, 2015 2.00 AM) but less than 24 hour time interval, then the appointment is split into two partitions and will be displayed appropriately on both the days.

### All-Day

Represents an appointment that is created for an entire day such as holiday events. It renders separately in an All-day row, a separate place for all-day appointments. In Timeline (horizontal) view, all-day appointment renders in the usual work cells, as no all-day cells are present in that view.

N> An all-day row is normally visible on the Scheduler, as the [showAllDayRow](/api/js/ejschedule#members:showalldayrow) property is set to true by default.

### Recurrence

Represents an appointment that is created for a certain time interval that occurs repeatedly in a daily, weekly, monthly, yearly or every weekday basis at the same time interval based on the recurrence rule. The other available options and validations that can be performed on recurrence appointments can be referred from [here](/aurelia/schedule/working-with-appointments#recurrence-options).

## CRUD operation

Appointments play a dynamic role within the Schedule control with which the users mostly interact. You can manipulate (add/edit/delete/drag/resize) the required appointments that reveals one of the main purpose of the Schedule control.

### Add/Edit Appointments

The appointments can be added/edited in the Scheduler using any one of the following ways,

* Quick window
* Inline creation/editing
* Default appointment window
* [Context menu](/aurelia/schedule/context-menu)
* Through programmatically

#### Quick Window

The Quick window usually pops out while single clicking on the Scheduler cells or appointments. It requires the user to enter the Subject to proceed with the appointment creation. It also includes an **Edit** **Appointment** option displayed at the bottom left corner – on selection which opens up the normal appointment window.

On single clicking the scheduler appointments, the pop-up that shows up contains the appointment information along with the other options that are listed below,

* Edit Appointment
* Edit Series (only for the recurrence appointments)
* Delete icon

The quick window option can be enabled/disabled by using [showQuickWindow](/api/js/ejschedule#members:showquickwindow) API, whereas its default value is set to **true**.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-show-quick-window="false" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"> </ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

N> Select multiple cells either using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>enter</kbd> key, so that the quick window opens up for the selected date/time range.

Another way to disable the quick window option at dynamic time can be achieved through the [cellClick](/api/js/ejschedule#events:cellclick) and [appointmentClick](/api/js/ejschedule#events:appointmentclick) events. The below code example shows the way to disable the quick appointment window only while clicking on the cells, but displays for appointments.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-show-quick-window="true" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-cell-click.trigger="onCellClick($event)"> </ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onCellClick(event) {
      let args = event.detail;
      args.cancel = true; // Prevents the display of quick window on clicking the cells.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

#### Inline Appointment Creation/Editing

Another easier way, for adding or editing the appointment’s subject alone can be achieved using inline Add/Edit support. It allows the user to add and edit the appointments inline.

To get familiar with inline Add mode, single click on any of the Scheduler cells or press `enter` key on the selected cells. When the inline adding mode is ON, a text box will get created within the clicked Scheduler cells with a blinking cursor in it, requiring the user to enter the subject of an appointment. Once the subject is entered, the appointment will be saved on pressing the `enter` key.

To enable inline edit mode, single click on any of the existing appointment’s subject, so that the user can edit the subject of that appointment. The edited subject of that appointment is then updated on pressing the `enter` key.

The inline option can be enabled/disabled on Scheduler by using the [allowInline](/api/js/ejschedule#members:allowinline) API, whereas its default value is set to **false**.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-allow-inline="true" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"> </ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

#### Enabling Inline Edit alone
It is possible to disable the inline appointment creation and enabling only the editing mode of inline by making use of the `cellClick` event. The below code example shows the way to disable the inline appointment creation while clicking on the cells, but appointments can be edited while clicking on it’s subject.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-allow-inline="true" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-cell-click.trigger="onCellClick($event)"> </ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onCellClick(event) {
        let args = event.detail;
       args.cancel = true; // Prevents inline appointment creation on clicking the cells.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

#### Default Appointment Window

The default appointment window is availed with options like

* Subject
* Start and End Time
* All-Day
* TimeZone (for both Start and End time)
* Repeat options
* Description

The other additional options available are listed below for which the appropriate API’s are needed to be configured to display these options on the appointment window.

* Location ([showLocationField](/aurelia/schedule/miscellaneous#showhide-location-field))
* Priority ([prioritySettings](/aurelia/schedule/working-with-appointments#priority))
* Categorize ([categorizeSettings](/aurelia/schedule/working-with-appointments#categorization))
* [Resources](/aurelia/schedule/resources)

The appointments can be created by double-clicking the Scheduler cells across the required time slots, which makes the Create Appointment window to pop-up. The start and end time fields will get automatically populated, according to the time-slot selection. Clicking on the done button in an appointment window will create the appointment for the selected time cells.

N> Select multiple cells both using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>Alt</kbd>+<kbd>N</kbd> key, so that the default appointment window opens up for the selected date/time range with the Start and End time fields automatically filled in.

To prevent the display of default appointment window on double clicking the Scheduler cells, either the [appointmentWindowOpen](/api/js/ejschedule#events:appointmentwindowopen) or [cellDoubleClick](/api/js/ejschedule#events:celldoubleclick) event can be used, within which the **args.cancel** needs to be set to true. This behavior is depicted in the below code example.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-appointment-window-open.trigger="onAppointmentWindowOpen($event)"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onAppointmentWindowOpen(event) {
        let args = event.detail;
       args.cancel = true; // prevents the display of default appointment window
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

#### Through Programmatically

You can add/edit the appointments dynamically through the public method [saveAppointment](/api/js/ejschedule#methods:saveappointment). It accepts the JSON Object data (either a new or updated appointment object) as its argument.

{% highlight html %}

<template>
    <div>
        <ej-button id="btnAdd" value="Add" e-on-click.trigger="addAppointment($event)">Add</ej-button>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    addAppointment(event) {
        //appointment details
        let appointment = {
            Subject: "Gym",
            StartTime: new Date("2015/11/7 03:30 AM"),
            EndTime: new Date("2015/11/7 04:30 AM")
        };

        //create the schedule object
        let schObj = $("#schedule").data("ejSchedule");
        //pass the JSON object in the public method
        schObj.saveAppointment(appointment);
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

### Delete Appointments

The appointments can be deleted in either of the following ways,

* Selecting an appointment and clicking the delete icon in the quick appointment window.
* Hovering the mouse over appointments and clicking on Inline delete option which is enabled by default for all the appointments.
* Selecting an appointment and pressing <kbd>Delete</kbd> key.
* Through Programmatically.

A pop-up with a confirmation message will get displayed before deleting an appointment, which can be either switched on/off using the API `showDeleteConfirmationDialog`. Also, the confirmation text in that pop-up can be customized as mentioned [here](/aurelia/schedule/globalization-and-localization#localization:localizing-specific-words).

**For example**, to localize only the delete confirmation message in the delete window -

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-current-date="11/07/2015" e-show-delete-confirmation-dialog="true" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    addAppointment(event) {
        //appointment details
        let appointment = {
            Subject: "Gym",
            StartTime: new Date("2015/11/7 03:30 AM"),
            EndTime: new Date("2015/11/7 04:30 AM")
        };

        //create the schedule object
        let schObj = $("#schedule").data("ejSchedule");
        //pass the JSON object in the public method
        schObj.saveAppointment(appointment);
    }
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

    attached() {
        let deleteCustomizationMessage = {
            DeleteConfirmation: "Do you want to delete this Event?", // customize the confirmation message
            MouseOverDeleteTitle: "Delete Event", // customize the delete window title
            RecurrenceDeleteTitle: "Delete Repeat Event" // customize the recurrence delete window title
        };

        // Extend only the required changes to the original locale collection
        $.extend(ej.Schedule.Locale["en-US"], deleteCustomizationMessage);
    }
}

{% endhighlight %}

N> All these CRUD operations on appointments (add/edit/delete) can also be done through the default [context menu](/aurelia/schedule/context-menu#default-menu-options) options **Add Appointment**, **Edit Appointment** and **Delete Appointment** which is available, when context menu settings is enabled within Scheduler.

#### Through Programmatically

You can delete the appointments dynamically using the method [deleteAppointment](/api/js/ejschedule#methods:deleteappointment), which accepts the Guid of the appointment or complete appointment data as its argument. The Guid is availed as one of the appointment element’s attribute.

#### Example 1 - Using GUID

The below code example depicts the way to delete the appointments using GUID programmatically by calling the **deleteAppointment** function within the [appointmentClick](/api/js/ejschedule#events:appointmentclick) event, which triggers whenever the user clicks on an appointment.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-appointment-click.trigger="onAppointmentClick($event)"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onAppointmentClick(event) {
        let args = event.detail;
        let schObj = $("#schedule").data("ejSchedule");
        schObj.deleteAppointment(args.appointment.Guid);
        // $(".e-appointment").eq(0).attr("guid") --> To get the guid attribute value of an element directly.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

#### Example 2 - Using Appointment object

The below code example depicts the way to delete the appointments using appointment data programmatically by calling the **deleteAppointment** function within the [appointmentClick](/api/js/ejschedule#events:appointmentclick) event, which triggers whenever the user clicks on an appointment.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-appointment-click.trigger="onAppointmentClick($event)"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onAppointmentClick(event) {
        let args = event.detail;
        let schObj = $("#schedule").data("ejSchedule");
        schObj.deleteAppointment(args.appointment);
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

## Handling Appointment Actions

It is possible to define some specific actions to take place before the CRUD operation occurs on the Scheduler appointments through the following available client-side events,

* [beforeAppointmentCreate](/api/js/ejschedule#events:beforeAppointmentCreate)
* [beforeAppointmentChange](/api/js/ejschedule#events:beforeAppointmentChange)
* [beforeAppointmentRemove](/api/js/ejschedule#events:beforeAppointmentRemove)

**beforeAppointmentCreate** – Triggers before saving a new appointment.

**beforeAppointmentChange** – Triggers when an appointment is edited and before it is being updated to the dataSource.

**beforeAppointmentRemove** – Triggers before deleting an existing appointment.

To stop the save, edit and delete actions on the Scheduler appointments, following code example can be used.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList" e-on-before-appointment-create.trigger="onAppointmentSave($event)" e-on-before-appointment-change.trigger="onAppointmentEdit($event)" e-on-before-appointment-remove.trigger="onAppointmentDelete($event)"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onAppointmentSave(event) {
        let args = event.detail;
        args.cancel = true; // cancels the save action on appointments.
    }

    onAppointmentEdit(event) {
        let args = event.detail;
        args.cancel = true; // cancels the edit action on appointments.
    }

    onAppointmentDelete(event) {
        let args = event.detail;
        args.cancel = true; // cancels the delete action on appointments.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

## Read Only

An interaction with the appointments of the Scheduler can be enabled/disabled through the [readOnly](/api/js/ejschedule#members:readonly) property. When the `readOnly` property is set to `true`, it is not possible to do any actions on the appointments, but you can navigate between the schedule dates, views and can also be able to see the appointment details in the quick window. By default, this property is set to `false`.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-read-only="true" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM")
            }]
        };
    }
}

{% endhighlight %}

N> When the `readOnly` property is set to true – double clicking the cells will open the appointment window filled with appointment details, which can be allowed to view but cannot be edited or saved.

## Drag and Drop

The appointment time can be modified through the drag and drop behavior, by dragging and dropping it to the new location, so that the start time and end time of the appointment gets changed automatically. We can enable/disable the drag and drop functionality through the `allowDragAndDrop` property. By default, it is set to `true`.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-allow-drag-and-drop="false" e-appointment-settings.bind="AppointmentList"> </ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM")
            }]
        };
    }
}

{% endhighlight %}

### Handling Drag Actions Dynamically

The drag and drop functionality can be handled with the following three events,

* [dragStart](/api/js/ejschedule#events:dragstart)
* [drag](/api/js/ejschedule#events:drag)
* [dragStop](/api/js/ejschedule#events:dragstop)

**dragStart** – Triggers when the appointments are started to drag from its source location.

**drag** – Triggers when the appointments are being dragged over.

**dragStop** – Triggers when the appointments are dropped on a destined location.

The following code example shows how to cancel the dragging functionality with the help of one of these events.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-on-drag-stop.trigger="onDragStop($event)" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onDragStop(event) {
        let = args = event.detail;
        args.cancel = true; // cancels the drag action on appointments.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM")
            }]
        };
    }
}

{% endhighlight %}

### External Drag and Drop

It is possible to drag and drop the external items to and fro the Scheduler control. This action is handled through the property [`appointmentDragArea`](/api/js/ejschedule#members:appointmentdragarea), which specifies the draggable area name stating whether the appointments can be dragged outside of the control or within it.

The following code example lets you drag and drop the external items from the tree view control to the Scheduler.

{% highlight html %}

<template>
    <!-- Treeview List -->
    <div class="col-md-2"> 
        <span class=""><b>Tutorials </b> </span>
        <ul ej-tree-view="e-allow-drag-and-drop:true;e-width:170;e-allow-drop-child:false;e-allow-drop-sibling:false;e-allow-drag-and-drop-across-control:true;" e-on-node-drag-start.trigger="onDragStart($event)" e-on-node-dropped.trigger="onDropped($event)" id="treeViewDrag">
            <li class="expanded" id="HTML">HTML
                <ul>
                    <li>Introduction</li>
                    <li>Editors</li>
                    <li>Styles</li>
                    <li>Formatting</li>
                    <li>Tables</li>
                </ul>
            </li>
        </ul>
    </div>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-on-drag-stop.trigger="onDragStop($event)" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
    <div class="cwindow">
        <ej-dialog id="customWindow" e-width="600px" e-target=".cwindow" e-height="auto" e-show-on-init="false" e-enable-model="true" e-title="Create Appointment" e-css-class="e-scheduledialog" e-enable-resize="false" e-allow-keyboard-navigation="false" e-on-close.trigger="clearFields($event)">
            <form id="custom">
                <table width="100%" cellpadding="5">
                    <tbody>
                        <tr>
                            <td>Subject:</td>
                            <td colspan="2">
                                <input id="subject" type="text" value="" name="Subject" style="width: 100%" readonly />
                            </td>
                        </tr>
                        <tr>
                            <td>Description:</td>
                            <td colspan="2">
                                <textarea id="customDescription" name="Description" rows="3" cols="50" style="width: 100%; resize: vertical"></textarea>
                            </td>
                        </tr>
                        <tr>
                            <td>StartTime:</td>
                            <td>
                                <input id="StartTime" type="text" value="" name="StartTime" />
                            </td>
                        </tr>
                        <tr>
                            <td>EndTime:</td>
                            <td>
                                <input id="EndTime" type="text" value="" name="EndTime" />
                            </td>
                        </tr>
                        <tr>
                            <td>Resource:</td>
                            <td colspan="2">
                                <input id="resource" type="text" value="" name="Resource" style="width: 100%" readonly />
                            </td>
                        </tr>
                        <tr style="display: none">
                            <td>ownerId:</td>
                            <td colspan="2">
                                <input id="ownerId" type="text" name="ownerId" />
                            </td>
                        </tr>
                    </tbody>
                </table>
            </form>
            <div>
                <button type="submit" onclick="cancel()" id="buttonCancel" style="float:right;margin-right:20px;margin-bottom:10px;"> Cancel</button>
                <button type="submit" onclick="save()" id="buttonSubmit" style="float:right;margin-right:20px;margin-bottom:10px;"> Save</button>
            </div>
        </ej-dialog>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

onDragStart(e) {
    let e = event.detail;
    if (e.targetElementData.parentId == "") return false;
}

onDropped(event) {
    let e = event.detail;
    if ($(e.target).parents(".e-schedule").length != 0) {
        let scheduleObj = $("#Schedule1").data("ejSchedule");
        let result = scheduleObj.getSlotByElement($(e.target));
        // set value to custom appointment window fields
        $("#subject").val(e.droppedElementData.text);
        $("#customDescription").val(e.droppedElementData.text);
        $("#StartTime").ejDateTimePicker({ value: new Date(result.startTime) });
        $("#EndTime").ejDateTimePicker({ value: new Date(result.endTime) });
        $("#resource").val(result.resources.text);
        $("#ownerId").val(result.resources.id);
        $("#customWindow").ejDialog("open");
    }
}

save() {
    let obj = {};
    let formElement = $("#customWindow").find("#custom").get(0);
    for (let index = 0; index < formElement.length; index++) {
        let columnName = formElement[index].name, $element = $(formElement[index]);
        if (columnName != undefined) {
            if (columnName == "Subject") let value = formElement[index].value;
            if (columnName == "Description") value = formElement[index].value;
            if (columnName == "StartTime") value = new Date(formElement[index].value);
            if (columnName == "EndTime") value = new Date(formElement[index].value);
            if (columnName == "ownerId") value = parseInt(formElement[index].value);
            if (columnName != "Resource") obj[columnName] = value;
        }
    }
    $("#customWindow").ejDialog("close");
    let object = $("#Schedule1").data("ejSchedule");
    object.saveAppointment(obj);
}

cancel() {
    $("#customWindow").ejDialog("close");
}

constructor() {
    this.AppointmentList = {
        //Array of JSON data configure in dataSource
        dataSource: [{
            Id: 1,
            Subject: "Music Class",
            StartTime: new Date("2015/11/7 09:00 AM"),
            EndTime: new Date("2015/11/7 10:00 AM")
        }, {
            Id: 2,
            Subject: "School",
            StartTime: new Date("2015/11/7 02:00 PM"),
            EndTime: new Date("2015/11/7 06:30 PM")
        }]
    };
}

{% endhighlight %}

## Resize

Resizing an appointment is another way to change its start and end time. Mouse hover on the appointments, so that the resizing handlers gets displayed on either sides of the appointment which allows resizing. The resizing functionality can be enabled/disabled by setting the [enableAppointmentResize](/api/js/ejschedule#members:enableappointmentresize) property. By default it is set to `true`.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-enable-appointment-resize="false" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM")
            }]
        };
    }
}

{% endhighlight %}

### Handling Resize Actions Dynamically

The appointment resizing functionality can be handled through the following three events,

* [resizeStart](/api/js/ejschedule#events:resizestart)
* [resize](/api/js/ejschedule#events:resize)
* [resizeStop](/api/js/ejschedule#events:resizestop)

**resizeStart** – Triggers when the appointments are started resizing from its original time.

**resize** – Triggers when the appointment resizing is in progress.

**resizeStop** – Triggers when the appointment resizing is done.

The following code example shows how to cancel the resizing functionality with the help of one of these events.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-on-resize-start.trigger="onResizeStart($event)" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    onResizeStart(event) {
        let args = event.detail;
        args.cancel = true; // Blocks the resize action on appointments.
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM")
            }]
        };
    }
}

{% endhighlight %}

## Categorization

It allows to differentiate the appointments with various categorize options and individual colors. You can also denote the status of the appointments using this categorize option and can specify your own user-defined category collection. It is also possible to select multiple categorize for a single appointment.

### Categorize Settings

The [categorizeSettings](/api/js/ejschedule#members:categorizesettings) holds the below categorize related properties such as,

* [enable](/api/js/ejschedule#members:categorizesettings-enable) - It accepts true or false value, denoting whether to enable/disable the categorize option. Its default value is `false`.
* [allowMultiple](/api/js/ejschedule#members:categorizesettings-allowmultiple) – It enables or disables the multiple selection of categories for each appointments in the appointment window as well as in the context menu. Its default value is `false`.
* [dataSource](/api/js/ejschedule#members:categorizesettings-datasource) – Binds the categorize dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview).

We have below 6 default values for Categorize dataSource collection.

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.CategorizeSettings = {
            enable: true, //Enable the categorize options
            allowMultiple: true, //enable multiple selection options
            //data source collection binding
            dataSource: [
                { text: "Blue Category", id: 1, color: "#43b496", fontColor: "#ffffff" },
                { text: "Green Category", id: 2, color: "#7f993e", fontColor: "#ffffff" },
                { text: "Orange Category", id: 3, color: "#cc8638", fontColor: "#ffffff" },
                { text: "Purple Category", id: 4, color: "#ab54a0", fontColor: "#ffffff" },
                { text: "Red Category", id: 5, color: "#dd654e", fontColor: "#ffffff" },
                { text: "Yellow Category", id: 6, color: "#d0af2b", fontColor: "#ffffff" }
            ],
            text: "text", //text mapper field
            id: "id", //id mapper field
            color: "color", //categorize color mapper field
            fontColor: "fontColor" //categorize appointment font color mapper field
        };
    }
}

{% endhighlight %}

The below categorize fields holds the appropriate column names from the dataSource - 

<table>
    <tr>
        <th>Field name<br/><br/></th>
        <th>Description<br/><br/></th>
    </tr>
    <tr>
        <td>id<br/><br/></td>
        <td>It holds the binding name for <b>id</b> field in the categorize dataSource<br/><br/></td>
    </tr>
    <tr>
        <td>text<br/><br/></td>
        <td>It holds the binding name for <b>text</b> field in the categorize dataSource<br/><br/></td>
    </tr>
    <tr>
        <td>color<br/><br/></td>
        <td>It holds the binding name for <b>color</b> field in the categorize dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>fontColor<br/><br/></td>
        <td>It holds the binding name for <b>fontColor</b> field in the categorize dataSource. This font color applies for the appointment.<br/><br/></td>
    </tr>
</table>

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-categorize-settings.bind="CategorizeSettings" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.CategorizeSettings = {
            enable: true, //Enable the categorize options
            allowMultiple: true, //enable multiple selection options
            //data source collection binding
            dataSource: [
                { text: "Blue Category", id: 1, color: "#43b496", fontColor: "#ffffff" },
                { text: "Green Category", id: 2, color: "#7f993e", fontColor: "#ffffff" },
                { text: "Orange Category", id: 3, color: "#cc8638", fontColor: "#ffffff" },
                { text: "Purple Category", id: 4, color: "#ab54a0", fontColor: "#ffffff" },
                { text: "Red Category", id: 5, color: "#dd654e", fontColor: "#ffffff" },
                { text: "Yellow Category", id: 6, color: "#d0af2b", fontColor: "#ffffff" }
            ],
            text: "text", //text mapper field
            id: "id", //id mapper field
            color: "color", //categorize color mapper field
            fontColor: "fontColor" //categorize appointment font color mapper field
        };
        this.AppointmentList = {
            categorize: "categorize",
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM"),
                categorize: "3",
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM"),
                categorize: "1,2,6" // Multiple categorize id passing 
            }]
        };
    }
}

{% endhighlight %}

## Priority

This option prioritize the appointments based on its importance and it can be differentiated with each individual icons/images. By default, there are some specific set of default priority collection and you can also customize it with your own priority collection.

### Priority Settings

The [prioritySettings](/api/js/ejschedule#members:prioritysettings) holds the below priority related properties such as,

* [enable](/api/js/ejschedule#members:prioritysettings-enable) - It accepts true or false value, denoting whether to enable/disable the priority option. Its default value is **false**.
* [template](/aurelia/schedule/templates#priority-settings-template) – Customize the priority icon/images using template options.
* [dataSource](/api/js/ejschedule#members:prioritysettings-datasource) – binds the priority dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview).

We have below 4 default values for priority dataSource collection.

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.PrioritySettings = {
            enable: true, //enable the priority option
            //Configure the priority data source
            dataSource: [
                { text: "None", value: "none" },
                { text: "High", value: "high" },
                { text: "Low", value: "low" }
            ],
            text: "text", //mapper field for text
            value: "value" //mapper field for value
        };
    }
}

{% endhighlight %}

The below priority fields holds the appropriate column names from the dataSource,

<table>
    <tr>
        <th>Field name<br/><br/></th>
        <th>Description<br/><br/></th>
    </tr>
    <tr>
        <td>text<br/><br/></td>
        <td>It holds the binding name for <b>text</b> field in the priority dataSource<br/><br/></td>
    </tr>
    <tr>
        <td>value<br/><br/></td>
        <td>It holds the binding name for <b>value</b> field in the priority dataSource.<br/><br/></td>
    </tr>
</table>

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-priority-settings.bind="PrioritySettings" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.PrioritySettings = {
            enable: true, //enable the priority option
            //Configure the priority data source
            dataSource: [
                { text: "None", value: "none" },
                { text: "High", value: "high" },
                { text: "Low", value: "low" }
            ],
            text: "text", //mapper field for text
            value: "value" //mapper field for value
        };
        this.AppointmentList = {
            //set the priority mapper field for appointment data collection
            priority: "priority",
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 09:00 AM"),
                EndTime: new Date("2015/11/7 10:00 AM"),
                priority: "low", //pass the priority value
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 02:00 PM"),
                EndTime: new Date("2015/11/7 06:30 PM"),
                priority: "high" //pass the priority value
            }]
        };
    }
}

{% endhighlight %}

## Search or Filter Appointments

### Appointment Search

The public method [searchAppointments](/api/js/ejschedule#methods:searchappointments) is used to search the appointments in the Scheduler dataSource. It contains the below four arguments such as search string, search field, filter operator and ignore case.

**searchString** - It is used to search the given word/sentence within the appointment data.

**fields** - It is the field with which the search operation takes place. It’s an optional argument.

**filterOperator** – It denotes the filter type like `contains`, `greaterthan` or `lessthan`. It’s an optional argument.

**ignoreCase** – It is a boolean value to set the search string as case sensitive or not. It’s an optional argument.

{% highlight html %}

<template>
    <ej-button id="btnSearch" e-on-click.trigger="btnClick($event)"></ej-button>
    <div id="grid1" />
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    btnClick(event) {
        let _searchString = $("#txtSearch").val();
        let schObj = $("#Schedule1").data("ejSchedule");
        // method to retrieve the appointment based on search string
        let result = schObj.searchAppointments(_searchString);
        showResult(result, _searchString);
    }
    showResult(list, _searchString) {
        if (!ej.isNullOrUndefined(list) && list.length != 0 && _searchString != "") {
            $("#grid1").show();
            $("#grid1").data("ejGrid") && $("#grid1").ejGrid("destroy");
            $("#grid1").ejGrid({
                allowScrolling: true,
                dataSource: list,
                allowPaging: true
            });
        }
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

### Appointment Filters

The appointments can be filtered or shortlisted based on the simple or complex conditions with four available properties such as **field**, **operator**, **value** and **predicate** which is passed to the public method [filterAppointments](/api/js/ejschedule#methods:filterappointments).

**field** - It is the field, with which the search operation takes place. It’s an optional argument.

**operator** – It is generally used to specify the [filter](/js/datamanager/filtering) type.

**value** – It is the filter keyword based on which the records are filtered.

**predicate** – To add more than one conditional query, need to use `and`, `or` [predicates](/js/datamanager/filtering#and-predicate).

{% highlight html %}

<template>
    <ej-button id="btnSearch" e-on-click.trigger="btnClick($event)"></ej-button>
    <div id="grid1" />
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    btnClick(event) {
        // Add the filter data as like in the below format
        let filter = [{
            field: "Subject", // field configure
            operator: "contains",
            value: "Music",
            predicate: "or" // predicate
        }, {
            field: "Subject", // field configure
            operator: "contains",
            value: "School",
            predicate: "or" // predicate
        }];

        let schObj = $("#Schedule1").data("ejSchedule");
        // Method to get the Filtered appointment
        let result = schObj.filterAppointments(filter);
        showResult(result);
    }
    showResult(list, _searchString) {
        if (!ej.isNullOrUndefined(list) && list.length != 0 && _searchString != "") {
            $("#grid1").show();
            $("#grid1").data("ejGrid") && $("#grid1").ejGrid("destroy");
            $("#grid1").ejGrid({
                dataSource: list,
                allowPaging: true
            });
        }
    }
    constructor() {
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM")
            }]
        };
    }
}

{% endhighlight %}

## Recurrence Options

There are scenarios where you require the same appointments to be repeatedly created for multiple days on daily, weekly, monthly, and yearly or on every weekday basis.

In appointment data collection, **recurrence** and **recurrenceRule** are dependent fields. While creating or binding the recurrence appointment, the **recurrence** field is set to **true** and **recurrenceRule** contains recurrence pattern in string format.

### Recurrence Rule

The recurrence appointments are created based on the recurrence rule. The RecurrenceRule is a string value that contains the details of the recurrence appointments like

* repeat type - daily/weekly/monthly/yearly/every weekday
* how many times it needs to be repeated
* the interval duration
* the time period to render the appointment, etc.,

It has the following properties based on which the recurrence appointments are rendered in the Schedule control with its respective time period.

<table>
    <tr>
        <th>S.No<br/><br/></th>
        <th>Property<br/><br/></th>
        <th>Purpose<br/><br/></th>
    </tr>
    <tr>
        <td>1<br/><br/></td>
        <td>FREQ<br/><br/></td>
        <td>Maintains the Repeat type value of the appointment. <br/><br/>(<b>Example</b>: Daily, Weekly, Monthly, Yearly, Every week day)<br/><br/>Example: <b>FREQ=DAILY</b>;INTERVAL=1<br/><br/></td>
    </tr>
    <tr>
        <td>2<br/><br/></td>
        <td>INTERVAL<br/><br/></td>
        <td>Maintains the interval value of the appointments.<br/><br/><b>For example</b>, when you create the daily appointment at an interval of 2, the appointments are rendered on the days Monday, Wednesday and Friday. (Creates an appointment on all days by leaving the interval of one day gap)<br/><br/>Example: FREQ=DAILY;<b>INTERVAL=2</b><br/><br/></td>
    </tr>
    <tr>
        <td>3<br/><br/></td>
        <td>COUNT<br/><br/></td>
        <td>It holds the appointment’s count value. <br/><br/><b>For example</b>, When the recurrence appointment count value is 10, which means that 10 instances of appointments are created in the recurrence series.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>COUNT=10</b><br/><br/></td>
    </tr>
    <tr>
        <td>4<br/><br/></td>
        <td>UNTIL<br/><br/></td>
        <td>This property is used to store the recurrence end date value. <br/><br/><b>For example</b>, when you set the end date of appointment as 11/30/2015, the UNTIL property holds the end date value denoting when the recurrence actually ends.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>UNTIL=11/30/2015</b><br/><br/></td>
    </tr>
    <tr>
        <td>5<br/><br/></td>
        <td>BYDAY<br/><br/></td>
        <td>It holds the <b>DAY</b> values, representing on which the appointments actually renders. <br/><br/><b>For example</b>, Create the weekly appointment, and select the day(s) from the day options (Monday/Tuesday/Wednesday/Thursday/Friday/Saturday/Sunday). When Monday is selected, the first two letters of the selected day “MO” is saved in the <b>BYDAY</b> property. When multiple days are selected, the values are separated by commas.<br/><br/>Example: FREQ=WEEKLY;INTERVAL=1;<b>BYDAY=MO,WE</b>;COUNT=10<br/><br/></td>
    </tr>
    <tr>
        <td>6<br/><br/></td>
        <td>BYMONTHDAY<br/><br/></td>
        <td>This property is used to store the date value of the Month, while creating the Month recurrence appointment.<br/><br/><b>For example</b>, when you create a Monthly recurrence appointment for every 3rd day of the month, then <b>BYMONTHDAY</b> holds the value 3 and creates the appointment on 3rd day of every month.<br/><br/>Example: FREQ=MONTHLY;<b>BYMONTHDAY=3</b>;INTERVAL=1;COUNT=10<br/><br/></td>
    </tr>
    <tr>
        <td>7<br/><br/></td>
        <td>BYMONTH<br/><br/></td>
        <td>This property is used to store the index value of the selected Month while creating the yearly appointments.<br/><br/><b>For example</b>, when you create the yearly appointment on June month, the index value of June month 6 will get stored in the BYMONTH field. The appointment is created on every 6th month of a year.<br/><br/>Example: FREQ=YEARLY;BYMONTHDAY=16;<b>BYMONTH=6</b>;INTERVAL=1;COUNT=10<br/><br/></td>
    </tr>
    <tr>
        <td>8<br/><br/></td>
        <td>BYSETPOS<br/><br/></td>
        <td>This property is used to store the index value of the week. <br/><br/><b>For example</b>, when you create the monthly appointment in second week of a month, the index value of the second week (2) is stored in BYSETPOS.<br/><br/>Example: FREQ=MONTHLY;BYDAY=MO;<b>BYSETPOS=2</b>;UNTIL=8/11/2015<br/><br/></td>
    </tr>
    <tr>
        <td>9<br/><br/></td>
        <td>WKST<br/><br/></td>
        <td>This property is used to store the start day value of a week.<br/><br/><b>For example</b>, when you render the workweek the “WKST” value is Monday.<br/><br/></td>
    </tr>
    <tr>
        <td>10 <br/><br/></td>
        <td>EXDATE<br/><br/></td>
        <td>EXDATE is used to hold the modified appointment date details (date value) in the recurrence appointment series.<br/><br/><b>For example</b>, when you change the recurrence appointment instance under the date “6/19/2015”, then this date is added to the recurrence rule EXDATE field. “EXDATE” is also used to differentiate the edited occurrence of the recurrence series for some internal process while doing the “Edit Series or Delete series” actions.<br/><br/>Example: FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;<b>EXDATE=6/18/2015,6/20/2015</b>;RECUREDITID=1651<br/><br/></td>
    </tr>
    <tr>
        <td>11<br/><br/></td>
        <td>RECUREDITID<br/><br/></td>
        <td>This property contains the Parent Id value of the edited appointment. It is used to track the edited appointment occurrence with its parent recurrence appointment series.<br/><br/><b>For example</b>, when you edit the particular occurrence of the recurrence appointment series, the “RECUREDITID” is added to that edited appointment depicting its parent Id.<br/><br/>Example:<br/><br/>FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;EXDATE=6/18/2015,6/20/2015;<b>RECUREDITID=1651</b><br/><br/></td>
    </tr>
</table>

To know more about other possible combinations of above specified recurrence rule properties, refer [here](http://www.syncfusion.com/kb/3719/what-is-recurrencerule-in-the-schedule-control).

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Recurrence mapper field
            recurrence: "Recurrence",
            recurrenceRule: "RecurrenceRule",
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM"),
                Recurrence: true, //enable recurrence options
                RecurrenceRule: "FREQ=DAILY;INTERVAL=1;COUNT=5" //Recurrence rule.
            }]
        };
    }
}

{% endhighlight %}

### Recurrence Validation

The default recurrence validation has been included for recurrence appointments similar to the one available in outlook. The validation occurs during the recurrence appointment creation, drag and drop or resizing of the recurrence appointments and also if any single occurrence changes. The validation can be disabled by setting the [enableRecurrenceValidation](/api/js/ejschedule#members:enablerecurrencevalidation) property to `false`.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-enable-recurrence-validation="false" e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.AppointmentList = {
            //Recurrence mapper field
            recurrence: "Recurrence",
            recurrenceRule: "RecurrenceRule",
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date("2015/11/7 06:00 AM"),
                EndTime: new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date("2015/11/7 9:00 AM"),
                EndTime: new Date("2015/11/7 02:30 PM"),
                Recurrence: true, //enable recurrence options
                RecurrenceRule: "FREQ=DAILY;INTERVAL=1;COUNT=5" //Recurrence rule.
            }]
        };
    }
}

{% endhighlight %}

N> You can parse the **RecurrenceRule** of an appointment from the server-side by making use of a new generic utility class **RecurrenceHelper**. Refer this [KB document](https://www.syncfusion.com/kb/5390/how-to-parse-the-recurrencerule-in-server-side).

### Recurrence Edit and delete options

The recurring appointments can be edited or deleted in three ways as below:

* Single occurrence
* Following appointments
* Entire series

#### Single occurrence

When an option "Only this Appointment" is selected, a single occurrence of the recurrence appointment alone will be edited or deleted.

#### Following appointments

When an option "Following Appointments" is selected, all the following events of the recurrence appointment from the current instance will be edited or deleted. The previous instances of the recurrence appointment before this current instances will be retained as it is on the Scheduler.

#### Entire series

The entire recurrence series will be edited / deleted, on selecting this option.

## Reminder

Reminder option notifies all the appointments before some specific time. By default, it notifies before 5 minutes. Each and every appointment triggers the [reminder](/api/js/ejschedule#events:reminder) event and can utilize this event for other user actions like mailing particular event to someone or to do any kind of manipulations with the reminder appointments and so on. The `reminderSettings` includes the following 2 properties namely,

* **enable** - To enable the reminder settings of the Schedule control, set the **enable** property as `true` within the [reminderSettings](/api/js/ejschedule#members:remindersettings) option.

* **alertBefore** - Accepts the integer value to denote the time, before how long the reminder should be notified to the user.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-reminder-settings.bind="ReminderSettings" e-on-reminder.trigger="reminderCustom()", e-appointment-settings.bind="AppointmentList"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    reminderCustom() {
        alert("Reminder Appointment");
    }
    constructor() {
        this.ReminderSettings = {
            enable: true, //enable the reminder options
            alertBefore: 10 //notify before 10 minutes
        };
        this.AppointmentList = {
            //Array of JSON data configure in dataSource
            dataSource: [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(new Date().setMinutes(new Date().getMinutes() + 11)), // new Date("2015/11/7 06:00 AM"),
                EndTime: new Date(new Date().setHours(new Date().getHours() + 1)) // new Date("2015/11/7 07:00 AM")
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(new Date().setHours(new Date().getHours() + 2)),
                EndTime: new Date(new Date().setHours(new Date().getHours() + 4))
            }]
        };
    }
}

{% endhighlight %}

N> Whenever the reminder setting is enabled in the Scheduler with some specific value (in minutes) assigned to the **alertBefore** property, the **reminder** event gets triggered before this specified value. It includes the reminder appointment’s entire information within its arguments.

## Block Time Intervals

It allows to block the particular timeslots in Schedule. When specific timeslots are blocked, the appointments that lies in that range can either be made read-only or else can be allowed to interact with the users based on the value assigned to the `isBlockAppointment` property.

### Blockout Settings

The [blockoutSettings](/api/js/ejschedule#members:blockoutsettings) holds the below block intervals related properties such as,

* [enable](/api/js/ejschedule#members:blocktimesettings-enable) - It accepts true or false value, denoting whether to enable/disable the block intervals option. It's default value is `false`.
* [templateId](/api/js/ejschedule#members:blockoutsettings-templateid) â€“ It applies the template design to block the intervals.
* [dataSource](/api/js/ejschedule#members:blockoutsettings-datasource) â€“ Binds the block intervals dataSource collection. This property should be assigned either with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview).

The below blockout fields holds the appropriate column names from the dataSource - 

<table>
    <tr>
        <th>Field name<br/><br/></th>
        <th>Description<br/><br/></th>
    </tr>
    <tr>
        <td>id<br/><br/></td>
        <td>It holds the binding name for <b>id</b> field in the blockout dataSource<br/><br/></td>
    </tr>
    <tr>
        <td>subject<br/><br/></td>
        <td>It holds the binding name for <b>subject</b> field in the blockout dataSource<br/><br/></td>
    </tr>
    <tr>
        <td>startTime<br/><br/></td>
        <td>It holds the binding name for <b>startTime</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>endTime<br/><br/></td>
        <td>It holds the binding name for <b>endTime</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>isBlockAppointment<br/><br/></td>
        <td>It holds the binding name for <b>isBlockAppointment</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>isAllDay<br/><br/></td>
        <td>It holds the binding name for <b>isAllDay</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>resourceId<br/><br/></td>
        <td>It holds the binding name for <b>resourceId</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
    <tr>
        <td>customStyle<br/><br/></td>
        <td>It holds the binding name for <b>customStyle</b> field in the blockout dataSource.<br/><br/></td>
    </tr>
</table>

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-blockout-settings.bind="BlockoutSettings"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.BlockoutSettings = {
            enable: true, //Enable the blockout options
            //data source collection binding
            dataSource: [{
                BlockId: 101,
                BlockStartTime: new Date(2014, 4, 5, 10, 00),
                BlockEndTime: new Date(2014, 4, 5, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true
            }, {
                BlockId: 102,
                BlockStartTime: new Date(2014, 4, 4, 12, 00),
                BlockEndTime: new Date(2014, 4, 4, 13, 00),
                BlockSubject: "Maintenance",
                IsBlockAppointment: true
            }],
            id: "BlockId",  //id mapper field
            startTime: "BlockStartTime",  //start time mapper field
            endTime: "BlockEndTime",  //end time mapper field
            subject: "BlockSubject",  //subject mapper field
            isBlockAppointment: "IsBlockAppointment"  //block appointment mapper field
        };
    }
}

{% endhighlight %}

### Blocking Appointments

The Appointments that lies within the blocked time range can be restricted to perform CRUD operations in it and can be made read-only. This can be achieved by setting [isBlockAppointment](/api/js/ejschedule#members:blockoutsettings-isblockappointment) property to true.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-blockout-settings.bind="BlockoutSettings"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.BlockoutSettings = {
            enable: true, //Enable the blockout options
            //data source collection binding
            dataSource: [{
                BlockId: 101,
                BlockStartTime: new Date(2014, 4, 5, 10, 00),
                BlockEndTime: new Date(2014, 4, 5, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true
            }],
            id: "BlockId",
            startTime: "BlockStartTime",
            endTime: "BlockEndTime",
            subject: "BlockSubject",
            //Bind the block appointment field in datasource
            isBlockAppointment: "IsBlockAppointment"
        };
    }
}

{% endhighlight %}

### Customizing block time intervals

The [blockoutSettings](/api/js/ejschedule#members:blockoutsettings) holds the below properties to customize the block intervals such as,

* [templateId](/api/js/ejschedule#members:blockoutsettings-templateid) - Template design that applies on the block intervals.
* [customStyle](/api/js/ejschedule#members:blockoutsettings-customstyle) - The custom CSS that applies on the blocked intervals.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-blockout-settings.bind="BlockoutSettings"></ej-schedule>
    </div>

    <script id="blockTemplate" type="text/x-jsrender">
        <div style="height:100%">
            <div>{{:BlockSubject}}</div>
        </div>
    </script>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.BlockoutSettings = {
            enable: true,
            templateId: "#blockTemplate",
            dataSource: [{
                BlockId: 101,
                BlockStartTime: new Date(2014, 4, 5, 10, 00),
                BlockEndTime: new Date(2014, 4, 5, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true
            }],
            id: "BlockId",
            startTime: "BlockStartTime",
            endTime: "BlockEndTime",
            subject: "BlockSubject",
            isBlockAppointment: "IsBlockAppointment"
        };
    }
}

{% endhighlight %}

### Blocking time interval based on resources

* [resourceId](/api/js/ejschedule#members:blockoutsettings-resourceid) - property used within the `blockoutSettings` which accepts the resource id's can be used to apply the block intervals based on the resources.

{% highlight html %}

<template>
    <div>
        <ej-schedule id="Schedule1" e-current-date="11/07/2015" e-group.bind="ScheduleGroup" e-resources.bind="ScheduleResources" e-blockout-settings.bind="BlockoutSettings" e-appointment-settings.bind="AppointmentSettings"></ej-schedule>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class Schedule {
    constructor() {
        this.ScheduleGroup: {
            resources: ["Owners"]
        };
        this.ScheduleResources =  [{
            field: "ownerId",
            title: "Owner",
            name: "Owners",
            allowMultiple: true,
            resourceSettings: {
                dataSource: [
                    { text: "Nancy", id: 1, color: "#f8a398" },
                    { text: "Steven", id: 2, color: "#56ca85"}
                ],
                text: "text", id: "id", color: "color"
            }
        }];
        this.BlockoutSettings = {
            enable: true, //Enable the blockout options
            //data source collection binding
            dataSource: [{
                BlockId: 101,
                BlockStartTime: new Date(2014, 4, 1, 10, 00),
                BlockEndTime: new Date(2014, 4, 1, 11, 00),
                BlockSubject: "Travel",
                IsBlockAppointment: true,
                BlockResId: 2
            }],
            id: "BlockId",
            startTime: "BlockStartTime",
            endTime: "BlockEndTime",
            subject: "BlockSubject",
            isBlockAppointment: "IsBlockAppointment",
            //resource id mapper field
            resourceId: "BlockResId"
        };
        this.AppointmentSettings = {
            dataSource: [{
                EventId: 100,
                EventSubject: "Research on Sky Miracles",
                EventStartTime: new Date(2014, 4, 2, 9, 00),
                EventEndTime: new Date(2014, 4, 2, 10, 30),
                ownerId: 2
            }],
            id: "EventId",
            startTime: "EventStartTime",
            endTime: "EventEndTime",
            subject: "EventSubject",
            resourceFields: "ownerId"
        }
    }
}

{% endhighlight %}
