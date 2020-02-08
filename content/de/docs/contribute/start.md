---
title: Der erste Beitrag
slug: start
content_template: templates/concept
weight: 10
card:
  name: contribute
  weight: 10
---

{{% capture overview %}}

Wenn Sie an der Dokumentation oder der Website von Kubernetes mitwirken möchten, helfen Ihnen diese Seite und die verlinkten Themen beim Start. Sie müssen kein Entwickler oder Autor technischer Beschreibungen sein, um einen großen Einfluss auf die Dokumentation von Kubernetes und die Benutzerfreundlichkeit zu haben. Alles was Sie brauchen ist ein [Konto bei GitHub](https://github.com/join) und ein Webbrowser.

Wenn Sie auf der Suche nach Informationen über die Mitwirkung am Quelltext von Kubernetes sind, richten Sie sich nach den [Kubernetes Community-Richtlinien](https://github.com/kubernetes/community/blob/master/governance.md).

{{% /capture %}}

{{% capture body %}}

## Grundlagen unserer Dokumentation

Die Dokumentation von Kubernetes ist in Markdown geschrieben und wird mittels Hugo verarbeitet und ausgerollt. Der Quelltext ist bei GitHub unter [https://github.com/kubernetes/website](https://github.com/kubernetes/website) verfügbar. Der Großteil der Dokumentation ist im Verzeichnis `/content/en/docs/` abgelegt. Einige Teile der Referenz-Dokumentation wird automatisch mittels der Skripte im Verzeichnis `update-imported-docs` erzeugt.

Über die Webseite von GitHub können Sie neue Issues anlegen, Inhalte bearbeiten und Änderungen anderer prüfen. Sie können auch die History-Funktion und die Suche von GitHub nutzen.

Nicht alle Aufgaben können über die Webseite von GitHub erledigt werden. Diese Aufgaben werden in den Contribution Guides für [Fortgeschrittene](/docs/contribute/intermediate/) und [Experten](/docs/contribute/advanced/) beschrieben.

### In den SIG Docs mitarbeiten

Die Dokumentation von Kubernetes wird von einer {{< glossary_tooltip text="Special Interest Group" term_id="sig" >}} (SIG) mit Namen SIG Docs gewartet. Wir [kommunizieren](#participate-in-sig-docs-discussions) über einen Slack-Kanal, eine Mailingliste und wöchentliche Videokonferenzen. Neue Teilnehmer sind willkommen. Für mehr Informationen siehe [Participating in SIG Docs](/docs/contribute/participating/).

### Rahmenbedingungen für Inhalte

Die Gemeinschaft SIG Docs hat Richtlinien erarbeitet, welche Inhalte in der Dokumentation von Kubernetes erlaubt sind. Lesen Sie [Documentation Content
Guide](/docs/contribute/style/content-guide/) um zu entscheiden, ob der Inhalt ihres Beitrags den Rahmenbedingungen entspricht. Sie können Fragen über die Richtlinien im [#sig-docs](#participate-in-sig-docs-discussions) Slack-Kanal stellen.

### Gestaltungsrichtlinien

Wir haben [Gestaltungsrichtlinien](/docs/contribute/style/style-guide/) mit Informationen über die Entscheidungen der SIG Docs-Gemeinschaft erarbeitet, in denen Grammatik, Syntax, Formatierung von Quelltext und typografische Konventionen festgehalten wird. Lesen Sie die Richtlinien bevor Sie ihren ersten Beitrag erstellen und wenn Sie Fragen haben.

Änderungen an den Gestaltungsrichtlinien werden von der Gruppe SIG Docs gemacht. Um eine Änderung vorzuschlagen, [fügen Sie sie der Agenda für eine der bevorstehenden Besprechungen hinzu](https://docs.google.com/document/d/1zg6By77SGg90EVUrhDIhopjZlSDg2jCebU-Ks9cYx0w/edit#) und nehmen Sie an dem Meeting teil. Siehe [advanced contribution](/docs/contribute/advanced/) für weitere Informationen.

### Seitenvorlagen

Wir verwenden Vorlagen für Seiten um die Darstellung der Dokumentation zu kontrollieren. Machen Sie sich mit der [Verwendung von Vorlagen](/docs/contribute/style/page-templates/) vertraut.

### Hugo Shortcodes

Die Dokumentation von Kubernetes wird mittels Hugo von Markdown zu HTML übersetzt. Wir verwenden sowohl die üblichen Hugo Shortcodes als auch speziell für die Dokumentation von Kubernetes erstellte. Siehe [Custom Hugo shortcodes](/docs/contribute/style/hugo-shortcodes/) für die Verwendung.

### Mehrsprachigkeit

Der Quelltext der Dokumentation ist in mehreren Sprachen im Verzeichnis `/content/` verfügbar. Jede Sprache hat ihr eigenes Verzeichnis mit einem Code bestehend aus zwei Buchstaben nach dem [ISO 639-1 Standard](https://www.loc.gov/standards/iso639-2/php/code_list.php). Die englische Dokumentation ist z.B. unter `/content/en/docs/` abgelegt.

Siehe [Localize content](/docs/contribute/intermediate#localize-content) für mehr Informationen über die Mitarbeit an der Dokumentation in mehreren Sprachen im Contribution Guide für Fortgeschrittene.

Wenn Sie Interesse an einer neuen Lokalisierung haben, lesen Sie [Localization](/docs/contribute/localization/).

{{% /capture %
