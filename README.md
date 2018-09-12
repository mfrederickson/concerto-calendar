# Concerto 2 Calendar Plugin
This plugin provides support for displaying Google Calendar or iCal entries in Concerto 2.

To install this plugin, go to the Plugin management page in concerto, select RubyGems as the source and "concerto_calendar" as the gem name.

Concerto 2 Calendar is licensed under the Apache License, Version 2.0.

## Frontend Styling the 'List Details' Output Format

Here is the styling that I like to use for output of this type.

```
@import url('https://fonts.googleapis.com/css?family=Kalam:300');

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

ul.cal {
  list-style: none;
  column-count: 3;
  column-gap: 2em;
  padding: 0 1em;
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
