# Concerto 2 Calendar Plugin
This plugin provides support for displaying Google Calendar or iCal entries in Concerto 2.

To install this plugin, go to the Plugin management page in concerto, select RubyGems as the source and "concerto_calendar" as the gem name.

Concerto 2 Calendar is licensed under the Apache License, Version 2.0.

## Output Formats

### List (Custom Template, Groups of 5)

This is the default item template for this output, if one is not specified.

```
<div class="event">
  <div class="event-title">#{title}</div>
  <div class="event-date">#{date}</div>
  <div class="event-time">#{time}</div>
  <div class="event-location">#{location}</div>
  <div class="event-description">#{description}</div>
</div>
```

### Detailed (Custom Template, Single)

This is the default item template for this output, if one is not specified.

```
<div class="event">
  <h1 class="event-title">#{title}</h1>
  <h2 class="event-date">#{date}</h2>
  <div class="event-time cal-time">#{time}</div>
  <div class="event-location cal-location">#{location}</div>
  <div class="event-description"><p>#{description}</p></div>
</div>
```

### List (Groups of 5)

This renders content similar to the following.  Each piece of content will contain up to 5 entries.

```
<h1>name of calendar</h1>

<!-- the h2 and dl repeat for each unique date -->
<h2 class='event-date'>date of event</h2>
<dl class='events'>

  <!-- the dt/dd entries repeat for each item in the same day -->
  <dt class='event-time'>event time</dt>
  <dd class='event-title'> #{item.name}</dd>

</dl>

```

_The dl and dt and dd tags are stripped out and not actually rendered, but their content is, so the content seems to run together._

### List (Events by Day)

This renders content similar to the following. All entries are placed in one piece of content.  A content name based class name in the outermost ul allows for unique styling for each calendar--  the name of your content when you created the calendar entry will be lowercased, dasherized, and cleaned up a little.  It is shown below as `your-content-name-here`.

```
<ul class='cal cal-detailed-list cal-your-content-name-here'>
  
  <!-- each day is a list item -->
  <li>
    <h2 class='event-date'>date of event</h2>
    <ul class='events'>

      <!-- each event on this day is a list item -->
      <li>
        <div class='event-time'>time of event</div>
        <div class='event-title'>title</div>
        <div class='event-description'>description</div>
        <div class='event-location'>location</div>
      </li>

    </ul>
  </li>

</ul>
```

Here is the styling that I like to use for output of this type, for a "menuboard" or calendar-at-a-glance view.

```
@import url('https://fonts.googleapis.com/css?family=Kalam');

ul.cal {
  list-style: none;
  column-count: 3;
  column-gap: 2em;
  padding: 0 1em;
}

ul.cal * {
  font-family: 'Kalam', cursive;
}

ul.cal li {
  break-inside: avoid;
  margin-top: 0;
}

ul.events {
  list-style: none;
  padding-left: 0;
  margin-bottom: .25em;
}

ul.events li {
  margin-bottom: .5em;
}

li.event-date h2 {
  padding-bottom: .1em;
  margin-bottom: .25em;
  margin-top: 0;
  border-bottom: solid 2px #222;
}

.event-time {
  display: inline-block;
}

.event-title {
  display: inline-block;
  font-weight: bold;
}

.event-location, .event-description {
  display: block;
  color: #777;
  font-size: 0.8em;
  padding-left: 3em;
}
```

You add the CSS to your template in Concerto by uploading the .css file when you edit your template.
