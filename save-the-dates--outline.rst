Save the Dates - Das Kalenderframework plone.app.event
======================================================

Johannes Raggam, BlueDynamics Alliance
Plonekonferenz, München, 2012


Who am I
--------

- Johannes Raggam, programmatic.pro
- BlueDynamics Alliance Partner seit 2010
- Zope seit 2002, Plone seit 2005

- 2002: Gründung g24.at
  - Online Community für Graz
  - Schwerpunkt auf Veranstaltungstermine
  - System: PostNuke

- 2012: Geplanter g24.at Relaunch auf Basis des Plone Frameworks


Plone ATEvent - die aktuelle Situation
--------------------------------------
% TODO: Bild ATEvent Form

- Veraltetes Date/Time Widget
- Keine Ganztagestermine
- Keine Wiederholungs/Recurring Regeln
- Ungenügende iCalendar Unterstützung
- Veraltete Infrastruktur: CMFCalendar, PloneTestCase.
- Verwobene Codebasis:
    Date/Time Widget und Tests in CMFPlone
    Portlets in plone.app.Portlets
    CMFCalendar Dependency


Erweiterungen und Verbesserungen
--------------------------------

% Alle auflisten, die wichtigsten erläutern

- Gruppierung von Events: MultiEvent, zopyx.multieventcalendar

- Teilnehmerverwaltung: EventRegistration, SignableEvent, collective.eventinviter, uwosh.timeslot, collective.inviting (gh)

- Terminwiederholungen: RecurringEvent, p4a.ploneevent

- Schemamodifikationen: medialog.eventcategory, redturtle.imagedevent, mxmCalendar

- Darstellung und Kalenderansichten: CalViews, CalendarX, Solgema.fullcalendar (gh), collective.js.fullcalendar, ftw.calendar, zettwerk.fullcalendar, cciaa.portlet.calendar, ATimeline, p4a.calendar (gh) (Plone4ArtistsCalendar)

- Import/Export: PloneiCalendar, Products.Calendaring, PloneRDFCalendar, collective.Calendaring, slc.calendarfetcher, p4a.plonecalendar (gh)

- Widgets: collective.calendarwidget, PloneZCdatetimeWidget, Products.DateFree, collective.portlet.datepicker, collective.z3cform.datetimewidget, Products.TimeRangeWidget, collective.experimental.pietimemenu, collective.atmultidateselectionfield, p4a.datetimewidgets, IntelliDateTime (at), MxDateTimeField (at), archetypes.recurringdate (at), archetypes.datetimewidget (gh)

- vs.event (recurrence, attendees, widget, all-day, suplementary events)
- CalPlone (ical im/export, attendees, recurrence, scheduling)
- mxmCalendarTypes (icalendar, attendees, todo/task contents, ...)

- Infrastruktur: plone.app.eventindex, bda.calendar.base, Products.DateRangeInRangeIndex, Products.DateRecurringIndex, bda.intellidatetime, collective.weighteddaterangeindex, dateable.chronos, dateable.kalends, experimental.daterangeindexoptimisations, experimental.ulocalized_time


plone.app.event - bringing it all together
------------------------------------------

plone.app.event ersetzt ATEvent und bietet diese Features:

- Alle Event- und Kalenderbezogenen Funktionalitäten in einem Pyhonpacket.
- Möglichst geringe Abhängigkeiten von Plone auf plone.app.event. Möglichkeit
  der Deinstallation.
- Aufsplittung generischer Funktionalitäten in seperate Packages.
- Archetypes Typ und Dexterity Behaviors.
- Gewährleistung der Funktionalität auch ohne Archetypes.
- iCalendar Standardkonformität.
- Modernisiertes Date/Time Widget.
- Unterstützung von Ganztagesterminen.
- Recurring Events.
- Zeitzonen Unterstützung.
- Modernisierung der Infrastruktur (plone.app.testing, plone.app.registry, ...)


Der lange Weg zu plone.app.event
--------------------------------

% TODO: recherche über die pre-Snowsprint historie

* ... Calendaring Sprint, USA, ...
* Snowsprint 2007, Vorarlberg: Dateable, Kalends.
* Cathedral Sprint 2010, Köln: plone.app.event.
* DZUG Tagung 2010, Dresden: Recurrence Widget refactoring.
* Plone Conference 2010 Bristol: Tests, Polishing.
* Artsprint 2011 Wien: Timezone support, Polishing.
* Buschenschanksprint 2011, Berghausen, Austria.
* BarSprint 2011, Ljubljana: Refactoring, icalendar Package, plone.app.eventindex.
* 10/2011 - 01/2012: Recurrence Widget, Dexterity Behaviors.
* Artsprint 2012: ...


plone.app.event - der derzeitige Status
---------------------------------------

% TODO Screenshots von Forms und Funktionalitäten, Screencasts.

- Generische Funktionalitäten in seperaten Packages
  % Konzept geht auf: plone.event wird von anderen Implementierungen benutzt,
  % Products.DateRecurringIndex ist austauschbar mit plone.app.eventindex,
  % icalendar wird abseits der Plone Welt genutzt, jquery.recurrenceinput ist
  % für jedes Webprojekt nutzbar.

% ATEvent & Dexterity Behaviors

% whole day events

% datetime widget

% recurring events

% Timezone support

% DateRecurringIndex / plone.app.eventindex

% Neues calendarportlet


plone.app.event - was fehlt noch
--------------------------------

% TODO: Testabdeckung
- Testabdeckung XXX %

- Finalisierung plone.forminput.datetime

- Dokumentation

- PLIP Submission.


plone.app.event - die API
-------------------------

- plone.event.recurrence
% TODO: recurrence_sequence_ical

- plone.event.utils
% TODO: normalize timezone
% TODO: pydt

- plone.app.event.base
% TODO: get timezone of context,
% TODO: get all events within a range

- plone.app.event.ical
% TODO: ical export example

- plone.app.event.interfaces
% TODO: ADAPTERS
%       IEventAccessor
%       IRecurrence
%       IICalendar


plone.app.event - the Future
----------------------------
- Abweichende Beginn-/Endzeiten und Texte bei Recurring Events
- Weitere iCalendar Standard Event Typen: Journal, Todo, Alarm
- iCalendar import
- CalDAV schnittstelle
- CardDAV/vCard schnittstelle


Try it!
-------

$ git clone git@github.com:collective/plone.app.event.git

READ: README.txt


Help out!
---------

Fork me. Submit Pull requests.

Tnx!
----
