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

### Umsetzbare Issues erstellen {#file-actionable-issues}

- **Für eine existierende Seite**

    Wenn Ihnen ein Problem mit einer existierenden Seite auffällt, gehen Sie zum Ende der Seite und klicken Sie auf den Button **Create an Issue**. Wenn Sie noch nicht bei GitHub angemeldet sind, melden Sie sich an. Ein Formular zum Anlegen eines GitHub Issues mit einigen vorausgefüllten Daten wird angezeigt.
    Verwenden Sie Markdown und füllen Sie so viele Einzelheiten wie möglich aus. An einigen Stellen werden leere Klammern (`[ ]`) angezeigt, in die Sie ein `x` einsetzen können um Ihre Auswahl anzuzeigen. Sollten Sie bereits eine Lösung für das Problem vorschlagen wollen, fügen Sie diese zu dem Issue hinzu.

- **Eine neue Seite vorschlagen**

    Wenn Sie denken, das eine bestimmte Seite angelegt werden sollte, aber nicht sicher sind, an welcher Stelle die Seite eingefügt werden kann oder wenn es keine passende Stelle gibt, können Sie trotzdem einen Issue erstellen. Sie können entweder eine existierende Seite in der Nähe des neuen Inhalts verwenden, um den Issue anzulegen oder Sie gehen direkt zu [https://github.com/kubernetes/website/issues/new/](https://github.com/kubernetes/website/issues/new/) und erstellen den Issue dort.

### Wie man großartige Issues erstellt

Um sicherzustellen, dass wir Ihren Issue verstehen und umsetzen können, folgen Sie diesen Richtlinien:

- Verwenden Sie die Vorlage für Issues und füllen Sie so viele Einzelheiten wie möglich aus.
- Erklären Sie die Auswirkung, die der Issue auf die Benutzer hat.
- Grenzen Sie den Issue gegenüber anderen Dingen ab, so dass die Aufgabe eine angemessene Größe bekommt. Sollte das nicht möglich sein, brechen Sie die Aufgabe in kleinere Aufgaben auf.
    Zum Beispiel ist hat eine Aufgabe wie "Korrigiere die Dokumentation zu Sicherheit" keine angemessene, überschaubare Größe, wohingegen "Details zu 'Restricting network access' hinzufügen" eine klaren umfang hat.
- Sollte es Abhängigkeiten zu anderen Issues oder einem Pull Request geben, können Sie diese entweder mit der vollständigen URL oder mit der Issue- bzw. Pull Request-Nummer mit einem vorangestellten `#` referenzieren. Zum Beispiel `Eingefügt durch #987654`.
- Seien Sie respektvoll. "Die Dokumentation zu X ist schlecht" ist weder hilfreich noch umsetzbar. Der [Code of Conduct](/community/code-of-conduct/) kommt auch bei der Interaktion innerhalb der Kubernetes GitHub Repositories zur Anwendung.

## Teilnahme an Diskussionen der SIG Docs

Das Team SIG Docs kommuniziert über die folgenden Wege:

- [Treten Sie dem Kubernetes Slack bei](http://slack.k8s.io/), betreten Sie den Kanal `#sig-docs`, wo wir über die Issues der Dokumentation in Echtzeit diskutieren. Stellen Sie sich vor!
-[Melden Sie sich an der `kubernetes-sig-docs` Mailingliste an](https://groups.google.com/forum/#!forum/kubernetes-sig-docs), wo allgemeinere Diskussionen stattfinden und offizielle Entscheidungen festgehalten werden.
- Machen Sie bei den [wöchentlichen SIG Docs](https://github.com/kubernetes/community/tree/master/sig-docs) Besprechungen mit, die über den Slack-Kanal und die Mailingliste angekündigt werden. Aktuell verwenden die Videokonferenzen die Anwendung Zoom, also müssen Sie den [Zoom client](https://zoom.us/download) oder Ihr Telefon verwenden.

{{< note >}}
Sie können die wöchentlichen Besprechungen auch über den [Kubernetes community meetings calendar](https://calendar.google.com/calendar/embed?src=cgnt364vd8s86hr2phapfjc6uk%40group.calendar.google.com&ctz=America/Los_Angeles) abonnieren.
{{< /note >}}

## Existierende Inhalte verbessern

Um existierende Inhalte zu verbessen, erstellen Sie einen _Pull Request (PR)_, nachdem Sie einen _Fork_ erstellt haben. Diese beiden Begriffe sind [spezifisch für GitHub](https://help.github.com/categories/collaborating-with-issues-and-pull-requests/). Sie müssen nicht alles darüber wissen, da Sie alles über Ihren Webbrowser erledigen können. Wenn Sie zum [intermediate docs contributor guide](/docs/contribute/intermediate/) kommen, brauchen Sie allerdings mehr Wissen über Begriffe von Git.

{{< note >}}
**Kubernetes Softwareentwickler**: Wenn Sie ein neues Feature für ein zukünftiges Release von Kubernetes dokumentieren, ist der Prozess anders. Siehe
[Document a feature](/docs/contribute/intermediate/#sig-members-documenting-new-features) für Richtlinien zum Prozess und Informationen zu Fristen.
{{< /note >}}

### Den CNCF CLA unterzeichnen {#sign-the-cla}

Bevor Sie Code oder Dokumentation zu Kubernetes beitragen können, **müssen** Sie den [Contributor guide](https://github.com/kubernetes/community/blob/master/contributors/guide/README.md) lesen und das [Contributor License Agreement (CLA) unterschreiben](https://github.com/kubernetes/community/blob/master/CLA.md). Keine Sorge - es dauert nicht lang!

### Finden Sie eine Stelle für einen Beitrag

Wenn Sie etwas bemerken, das Sie sofort beheben möchten, folgen Sie den Anweisungen unten. Sie brauchen dafür keinen [Issue zu erstellen](#file-actionable-issues) (Sie dürfen aber auch).

Wenn Sie an einem bereits bestehenden Issue arbeiten möchten, gehen Sie zu [https://github.com/kubernetes/website/issues](https://github.com/kubernetes/website/issues) und suchen Sie nach einem Issue mit dem Schlagwort `good first issue` (Sie können [diesen](https://github.com/kubernetes/website/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22) Link verwenden). Lesen Sie die Kommentare und stellen Sie sicher, dass es nicht bereits einen offenen Pull Request für den Issue gibt und das niemand einen Kommentar hinterlassen hat, dass er bereits an dem Issue arbeitet (3 Tage sind ein guter Zeitraum). Schreiben Sie einen Kommentar, dass Sie gerne an dem Issue arbeiten möchten.

### Den Git Branch auswählen

Der wichtigste Aspekt für das Stellen eines Pull Requests ist die Auswahl des Branches, auf dem Sie Ihren Beitrag basieren. Die folgenden Richtlinien helfen Ihnen bei der Entscheidung:

- Verwenden Sie `master` um Probleme mit Inhalten zu beheben, die bereits veröffentlicht wurden oder um Verbesserungen an Inhalten vorzunehmen, die bereits existieren.
- Verwenden Sie `master` um Dinge zu dokumentieren, die Teil des aktuellen Release von Kubernetes, aber noch nicht dokumentiert sind. Sie sollten Inhalte als erstes in Englisch schreiben, und das Übersetzungsteam wird eine Aufgabe zur Übersetzung erstellen.
- Sollten Sie an Übersetzungen arbeiten, sollten Sie den Konventionen für die Übersetzung folgen. Sie finden diese heraus, in dem Sie andere Pull Requests ansehen (Tipp: Suchen Sie nach `is:pr is:merged label:language/de`).
  - Einige Übersetzungsteams arbeiten mit PRs mit dem Zielbranch `master`
  - Einige Übersetzungsteams arbeiten mit einer Serie von lang-laufenden Branches, und mergen diese regelmässig in `master`. Diese Art von Branch hat einen Namen wie `dev-\<version>-\<language code>.\<team milestone>`; zum Beispiel: `dev-{{< release-branch >}}-ja.1`.
- Wenn Sie Dokumentation für ein Feature Change Release schreiben oder aktualisieren, müssen Sie vorher die Major- und Minor-Version von Kubernetes kennen, in der die Änderung zuerst aufgenommen wird.
  - Zum Beispiel, wenn das Feature Gate *JustAnExample* im nächsten Minor-Release von Alpha zu Beta wechselt, müssen Sie die nächste Minor-Version kennen.
  - Finden Sie den Release Branch, der nach der Version benannt ist. Zum Beispiel werden Features, die im v{{< release-branch }} geändert werden, werden im Branch `dev-{{< release-branch >}}` dokumentiert.

Wenn Sie unsicher sind, welchen Branch Sie verwenden sollen, fragen Sie im Kanal `#sig-docs` im Slack oder bei einem der wöchtentlichen Besprechungen der SIG Docs nach.

{{< note >}}
Wenn Sie bereits einen Pull Request erstellt haben, und Sie wissen, dass der ausgewählte Branch falsch war, können Sie (und nur Sie, der Ersteller) den Branch ändern.
{{< /note >}}

### Einen Pull Request erstellen

Folgen Sie diesen Schritten, um einen Pull Request zu erstellen um die Kubernetes-Dokumentation zu verbessern:

1.  Klicken Sie auf der Seite, die Sie verbessern möchten, auf das Symbol eines Bleistifts oben rechts.
    Eine neue GitHub Seite mit Hilfestellungen wird geöffnet.
2.  Sollten Sie noch nie einen Fork der Dokumentation von Kubernetes erstellt haben, werden Sie aufgefordert, dies jetzt zu tun. Erstellen Sie den Fork unter Ihrem GitHub Benutzernamen, statt unter eine Organisation, in der Sie eventuell Mitglied sind. Der Fork hat üblicherweise eine URL wie `https://github.com/<username>/website`, wenn Sie kein Repository mit dem gleichen Namen haben.

    Der Grund für die Erstellung des Forks ist, das Sie keine Berechtigung haben, einen Branch direkt in das Repository von Kubernetes zu pushen.

3.  Der GitHub Markdown-Editor wird mit dem Quelltext der Markdown-Datei geöffnet.
    Machen Sie Ihre Änderungen. Füllen Sie das Formular **Propose file change** unter dem Editor aus. Das erste Feld ist eine Zusammenfassung Ihrer Commit-Meldung und sollte nicht länger als 50 Zeichen sein. Das zweite Feld ist optional, aber Sie können dort mehr Einzelheiten aufnehmen, falls Sie möchten.

    {{< note >}}
Fügen Sie keine Referenzen zu anderen GitHub Issues oder Pull Request in Ihre Commit Message auf. Sie können diese später in der Beschreibung des Pull Requests aufnehmen.
{{< /note >}}

    Klicken Sie auf **Propose file change**. Die Änderung wird automatisch als Commit in einem neuen Branch, mit einem Namen wie `patch-1`, in Ihrem Fork gespeichert.

4.
{{% /capture %}}
