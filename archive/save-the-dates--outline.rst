Save the Dates - Das Kalenderframework plone.app.event
======================================================

Johannes Raggam, programmatic.pro
BlueDynamics Alliance
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


Über diesen Talk
----------------

Termin- und Kalenderimplementierung in Plone.

Derzeit: Products.Archetypes' ATEvent. Veraltet.

Zukunft: plone.app.event.

* Geschichte.
* Aktuelle Situation.
* Plone.app.Event.
* Zukunft von plone.app.event.


Plone ATEvent - die aktuelle Situation
--------------------------------------

- Veraltetes Date/Time Widget
- Keine Ganztagestermine
- Keine Terminwiederholungen
- Keine Zeitzonen
- Ungenügende iCalendar Unterstützung
- Veraltete Infrastruktur: CMFCalendar, PloneTestCase.
- Verwobene Abhängigkeiten:
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


plone.app.event - bringing it all together
------------------------------------------

% TODO: screenshots

Archetypes und Dexterity Unterstützung

    Archetypes Inhaltstyp
    Dexterity Behaviors:
        Basistermin, Termin mit Recurrence, Termin mit Location,
        Termin mit Teilnehmer, Termin mit Kontaktadresse
    Dexterity Beispielstyp
        Generic Setup Konfiguration auf Basis der Behaviors

    Views, Search API, Catalog unterstützen beide Typen

Kapselung und Unabhängigkeit

    Event- und Kalenderbezogene Funktionalitäten in dedizierten Paketen:
        Dropped:
            Products.CMFPlone.CalendarTool XXX
            plone.app.controlpanel.event XXX
            Products.CMFPlone. datewidget, eventview
            Products.ATConentTypes: event type, ics_view
        Used:
            plone.app.event: dx, at, icalendar, configlet XXX, views
            Products.DateRecurringIndex / plone.app.eventindex
            plone.formwidget.recurrenceinput
            plone.formwidget.datetime
            plone.event: tools, recurrence calculations
            icalendar
            python-dateutil: rfc2445 recurrence

    Möglichst geringe Abhängigkeiten auf plone.app.event (Make it deinstallable)

    Keine fixe Abhängigkeit auf Archetypes sowie Dexterity. Future proof.

  % Konzept geht auf: plone.event wird von anderen Implementierungen benutzt,
  % Products.DateRecurringIndex ist austauschbar mit plone.app.eventindex,
  % icalendar wird abseits der Plone Welt genutzt, jquery.recurrenceinput ist
  % für jedes Webprojekt nutzbar.

Standards Compliance

    icalendar Standard, RFC5545: Recurrence, ical Export.
    Weitere mögliche Standards:
        CalDAV, vCard, CardDAV

Modernisiertes Date/Time Widget

    jquerytools Dateinput
    HTML5 Kompatibel

Unterstützung von Ganztagesterminen.
    
    Start: 0:00
    Ende: 23:59:59

Recurring Events

    icalendar Konforme Recurring Unterstützung
    Basierend auf python-dateutil
    Drop-In Replacement des Index: Products.DateRecurringIndex
    Recurrence Widget

Zeitzonen Unterstützung

    Integration von pytz.
    Olson Database - de facto Standard.

Kalenderportlet
    
    Unterstützung von Dexterity und Archetypes basierten Inhalten
    Recurrence Unterstützung

Modernisierung der Infrastruktur
    
    plone.app.testing
    plone.app.registry


plone.app.event - was fehlt noch
--------------------------------

% TODO: Testabdeckung
- Testabdeckung XXX %

- Migrationen

- Finalisierung Index-Benchmarks

- Finalisierung plone.forminput.datetime

- Weniger dringende TODOs.

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

% TODO: how to install

READ: README.txt


Help out!
---------

Fork me. Submit Pull requests. Sponsor a sprint.

Tnx!
----
