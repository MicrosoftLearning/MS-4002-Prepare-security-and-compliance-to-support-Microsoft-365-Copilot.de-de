# Lernpfad 1, Lab 3, Übung 1: Verwalten von DLP-Richtlinien  

In Ihrer Rolle als Holly Dickson, der neuen Microsoft 365-Administratorin von Adatum, haben Sie Microsoft 365 in einer virtualisierten Laborumgebung bereitgestellt. Wenn Sie mit Ihrem Microsoft 365-Pilotprojekt fortfahren, sind Ihre nächsten Schritte die Implementierung von DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust) bei Adatum. Zunächst erstellen Sie in dieser Übung eine benutzerdefinierte DLP-Richtlinie, und dann testen Sie DLP-Richtlinien im Zusammenhang mit der E-Mail-Nachrichtenarchivierung und E-Mails mit vertraulichen Daten. 

### Aufgabe 1 – Erstellen einer DLP-Richtlinie mit benutzerdefinierten Einstellungen

In dieser Aufgabe erstellen Sie eine Richtlinie zur Verhinderung von Datenverlust im Microsoft Purview-Portal, um sensible Daten vor der Weitergabe durch Benutzende zu schützen. Die von Ihnen erstellte DLP-Richtlinie informiert Ihre Benutzenden darüber, ob sie Inhalte teilen möchten, die IP-Adressen enthalten. 

Die Richtlinie enthält zwei Regeln oder Aktionen, von denen jede von der Anzahl der IP-Adressen in der Nachricht abhängig ist. Wenn die Nachricht eine IP-Adresse enthält, benachrichtigt die Richtlinie Personen mit einem Richtlinientipp und sendet weiterhin eine E-Mail an die Nachricht. Enthält der Inhalt jedoch zwei oder mehr IP-Adressen, wird die Nachricht blockiert, eine E-Mail mit hoher Sensibilitätsstufe zu dem Vorfall an die Absendenden gesendet und ein Richtlinientipp angezeigt, der es den Absendenden ermöglicht, die E-Mail-Blockierung aufzuheben, wenn sie im Richtlinientipp eine geschäftliche Begründung angeben.

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson** angemeldet sein. 

2. In **Microsoft Edge** sollte das Microsoft Purview-Portal weiterhin geöffnet sein. Wenn nicht, öffnen Sie dann eine neue Registerkarte, und navigieren Sie zu **https://compliance.microsoft.com**.

3. Wählen Sie im Portal **Microsoft Purview** im Navigationsbereich **Lösungen**, **Verhinderung von Datenverlust** und dann **Richtlinien**.

4. Auf der Seite **Richtlinien** wählen Sie in der Menüleiste die Option **+Richtlinie erstellen**, um den Assistenten **Richtlinie erstellen** zu starten.

5. Auf der Seite **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** zeigt die Spalte **Kategorien** die Richtlinienkategorien an. Jede Richtlinienkategorie bietet Vorlagen, die für die Erstellung dieser Art von Richtlinien verwendet werden können, mit Ausnahme der Kategorie **Benutzerdefiniert**. Diese Kategorie enthält keine bestimmte Vorlage; stattdessen können Organisationen benutzerdefinierte Richtlinien von Grund auf neu erstellen. Wenn Sie eine Kategorie auswählen, erscheint die Spalte **Vorlagen**, in der die verfügbaren Vorlagen für die ausgewählte Kategorie angezeigt werden. Wenn Sie eine Vorlage auswählen, wird eine weitere Spalte angezeigt, in der der Informationstyp angezeigt wird, der in dieser Vorlage geschützt ist. <br/> 

    Wählen Sie zum Beispiel **Finanzen** im Seitenbereich und blättern Sie dann durch die verschiedenen Vorlagen, die Sie in der Spalte **Vorlagen** auswählen können. Wählen Sie eine oder zwei der Vorlagen aus, um zu sehen, welche Art von Informationen sie schützt. Wenn Sie möchten, wählen Sie jede der verbleibenden Kategorien aus, um zu sehen, welche Art von Vorlagen bereitgestellt werden. 
  
6. Für diese Übung erstellen Sie eine benutzerdefinierte DLP-Richtlinie. Wählen Sie in der Spalte **Kategorien** die Option **Benutzerdefiniert**, wählen Sie in der Spalte **Vorlagen** die Vorlage **Benutzerdefinierte Richtlinie** und wählen Sie dann **Weiter**.

7. Geben Sie auf der Seite **DLP-Richtlinie benennen** die folgenden Informationen ein und wählen Sie dann **Weiter**:  <br/>

      - Name: **DLP-Richtlinie der IP-Adresse**
      - Beschreibung: **Diese Richtlinie erkennt das Vorhandensein von IP-Adressen in E-Mails. Endbenutzende werden über die Erkennung benachrichtigt und Admins erhalten eine Benachrichtigung. E-Mails mit 2 oder mehr IP-Adressen werden blockiert.**

8. Wählen Sie auf der Seite **Admineinheiten zuweisen** **Weiter**. 

9. Vergewissern Sie sich auf der Seite **Auswählen, wo die Richtlinie zugewiesen werden soll**, dass der **Status** für die folgenden Standorte auf **Ein** festgelegt ist (wenn einer dieser Standorte nicht standardmäßig auf **Ein** festgelegt ist, dann legen Sie ihn jetzt auf **Ein** fest): <br/>

    - **Exchange-E-Mail**
    - **SharePoint-Websites**
    - **OneDrive Konten**
    - **Teams-Chats und -Kanalnachrichten**

    Legen Sie alle anderen Orte auf **Aus** fest und wählen Sie dann **Weiter**.

10. Auf der Seite **Richtlinieneinstellungen definieren** sollte die Option **DLP-Regeln erstellen oder anpassen** standardmäßig festgelegt sein (wenn sie nicht bereits standardmäßig ausgewählt ist, dann wählen Sie sie jetzt aus) und wählen Sie dann **Weiter** aus. 

11. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** in der Menüleiste die Option **+ Regel erstellen**.

12. Auf der Seite **Regel erstellen** geben Sie die folgenden Informationen ein:
    
      - Name: **Regel für einzelne IP-Adressen**
    
      - Beschreibung: **E-Mail enthält eine IP-Adresse**
    
      - Wählen Sie im Abschnitt **Bedingungen** die Option **+ Bedingung hinzufügen** und wählen Sie dann **Inhalt enthält** aus dem erscheinenden Dropdownmenü. Geben Sie dann die folgenden Bedingungseinstellungen ein:
    
        - Wählen Sie im Feld **Inhalt enthält** das Dropdownmenü **Hinzufügen** und wählen Sie dann **Typen vertraulicher Informationen**.
        
        - Im Bereich **Typen vertraulicher Informationen** geben Sie **IP** in das Feld **Suche** ein und drücken dann die Eingabetaste.
        
        - Aktivieren Sie in den Suchergebnissen das Kontrollkästchen **IP-Adresse** und wählen Sie dann **Hinzufügen**.
        
     - Scrollen Sie zum Abschnitt **Benutzerbenachrichtigungen** und legen Sie den Umschalter **Benachrichtigungen verwenden, um Ihre Benutzenden zu informieren und sie über den richtigen Umgang mit sensiblen Daten aufzuklären** auf **Ein** fest.

    - Markieren Sie das Kontrollkästchen **Benutzer im Office 365-Dienst mit einem Richtlinientipp benachrichtigen**. Aktivieren Sie im Abschnitt **Richtlinientipps** das Kontrollkästchen **Richtlinientext anpassen**. 

        - Holly möchte, dass Sie die Nachricht mit dem Richtlinientipp anpassen. Geben Sie dazu den folgenden Text in dieses Feld ein: **ACHTUNG! Sie haben in dieser Nachricht vertrauliche Informationen (eine IP-Adresse) eingegeben. Sie können diese Nachricht zwar senden, sollten aber überprüfen, ob die Empfangenden berechtigt sind, diese vertraulichen Daten einzusehen.** 

    - Aktivieren Sie das Kontrollkästchen **Richtlinienhinweis vor dem Senden als Dialogfeld für die Endbenutzenden anzeigen (nur für Exchange-Workload verfügbar)**. 
    
    - Vergewissern Sie sich im Abschnitt **Vorfallsberichte**, dass der Umschalter **Benachrichtigung an Admins senden, wenn eine Regelübereinstimmung auftritt** auf **Ein** festgelegt ist (falls erforderlich, legen Sie ihn auf **Ein** fest).

    - Wählen Sie unten auf der Seite die Schaltfläche **Speichern** aus.

13. Auf der Seite **Erweiterte DLP-Regeln anpassen** sollte nun die **Einzelne IP-Adressregel** erscheinen, die Sie gerade erstellt haben. Wählen Sie die Option **+ Regel erstellen**, um die zweite DLP-Regel zu erstellen. 

14. Auf der Seite **Regel erstellen** geben Sie die folgenden Informationen ein:
    
    - Name: **Regel für mehrere IP-Adressen**
    
    - Beschreibung: **E-Mail enthält zwei oder mehr IP-Adressen**
    
    - Wählen Sie im Abschnitt **Bedingungen** die Option **+ Bedingung hinzufügen** und wählen Sie dann **Inhalt enthält** aus dem erscheinenden Dropdownmenü. Geben Sie dann die folgenden Bedingungseinstellungen ein:
    
        - Wählen Sie im Feld **Inhalt enthält** das Dropdownmenü **Hinzufügen** und wählen Sie dann **Typen vertraulicher Informationen**.
        
        - Im Bereich **Typen vertraulicher Informationen** geben Sie **IP** in das Feld **Suche** ein und drücken dann die Eingabetaste.
        
        - Aktivieren Sie das Kontrollkästchen **IP-Adresse** und wählen Sie dann **Hinzufügen**.

        - Unter dem Abschnitt **Typen vertraulicher Informationen** wird der Infotyp **IP-Adresse** angezeigt. Auf der rechten Seite der Zeile IP-Adresse wird die **Instanzanzahl** von **1** auf **beliebig** festgelegt. Ändern Sie den Wert des ersten Feldes von 1 auf **2**. Durch diese Änderung gilt diese Regel nur, wenn 2 oder mehr IP-Adressen in der E-Mail angezeigt werden. 
    
    - Wählen Sie im Abschnitt **Aktionen** die Option **+ Aktion hinzufügen**. Wählen Sie im angezeigten Dropdownmenü die Option **Zugriff einschränken oder Inhalte an Microsoft 365-Standorten verschlüsseln**. Geben Sie dann die folgenden Aktionseinstellungen ein:

    - Wenn unter dem Abschnitt **Zugriff einschränken oder Inhalte an Microsoft 365-Speicherorten verschlüsseln** keine Optionen angezeigt werden, dann wählen Sie ihn jetzt aus, um diesen Abschnitt zu erweitern. In diesem Abschnitt sollte die Option **Benutzer für den Empfang von E-Mails oder den Zugriff auf gemeinsame SharePoint-, OneDrive- und Teams-Dateien sperren** angezeigt werden, die standardmäßig aktiviert ist. Lassen Sie diese Option ausgewählt.

    - Wählen Sie unter der Option **Benutzer für den Empfang von E-Mails oder den Zugriff auf gemeinsame SharePoint-, OneDrive- und Teams-Dateien sperren** die Option **Alle sperren**.
    
    - Legen Sie im Abschnitt **Benutzerbenachrichtigungen** den Umschalter **Benachrichtigungen verwenden, um Ihre Benutzenden zu informieren und sie über den richtigen Umgang mit sensiblen Daten aufzuklären** auf **Ein** fest. 

    - Markieren Sie das Kontrollkästchen **Benutzer im Office 365-Dienst mit einem Richtlinientipp benachrichtigen**. Aktivieren Sie im Abschnitt **Richtlinientipps** das Kontrollkästchen **Richtlinientext anpassen**. 

        - Holly möchte, dass Sie die Nachricht mit dem Richtlinientipp anpassen. Geben Sie daher den folgenden Text in dieses Feld ein: **ACHTUNG! Sie haben in dieser Nachricht vertrauliche Informationen (mehrere IP-Adressen) eingegeben. Wenn Sie versuchen, diese Nachricht zu senden, werden Sie blockiert. Wenn Sie diese Blockierung aufheben, bedeutet dies, dass Sie die Übermittlung dieser vertraulichen Daten an die Empfangenden autorisiert haben.** 

    - Aktivieren Sie das Kontrollkästchen **Richtlinienhinweis vor dem Senden als Dialogfeld für die Endbenutzenden anzeigen (nur für Exchange-Workload verfügbar)**. 
    
    - Aktivieren Sie im Abschnitt **Benutzerüberschreibungen** das Kontrollkästchen **Überschreibungen von Microsoft 365-Dateien und Microsoft Fabric-Objekten zulassen**. Dadurch werden zusätzliche Einstellungen aktiviert, die angeben, wie Überschreibungen behandelt werden. Aktivieren Sie die einzelnen Kontrollkästchen für die folgenden beiden Optionen:

        - **Für die Außerkraftsetzung eine geschäftliche Begründung anfordern**
        - **Regel automatisch außer Kraft setzen, wenn sie dies als falsch positiv melden**
    
    - Vergewissern Sie sich im Abschnitt **Vorfallsberichte**, dass der Umschalter **Benachrichtigung an Admins senden, wenn eine Regelübereinstimmung auftritt** auf **Ein** festgelegt ist (falls erforderlich, legen Sie ihn auf **Ein** fest).

    - Wählen Sie unten auf der Seite die Schaltfläche **Speichern** aus.

15. Auf der Seite **Erweiterte DLP-Regeln anpassen** sollten nun sowohl die Regel **Eine IP-Adresse** als auch die Regel **Mehrere IP-Adressen** erscheinen. Wählen Sie **Weiter** aus.

16. Wählen Sie auf der Seite **Richtlinienmodus** die Option **Richtlinie sofort einschalten** und wählen Sie dann **Weiter**.

17. Auf der Seite **Prüfen und beenden** überprüfen Sie die soeben erstellte Richtlinie. Wenn etwas korrigiert werden muss, wählen Sie die entsprechende **Bearbeiten**-Option und nehmen Sie Ihre Korrekturen vor. Wenn alles in Ordnung ist, wählen Sie **Senden**.

18. Es kann etwa eine Minute dauern, bis die Seite **Neue Richtlinie erstellt** erscheint. Wenn dies der Fall ist, wählen Sie **Fertig**.

19. Lassen Sie Ihren Edge-Browser geöffnet. Schließen Sie keine der Registerkarten.


Sie haben nun eine DLP-Richtlinie erstellt, die in E-Mails und Dokumenten, die in Ihrer Organisation gesendet oder freigegeben werden, nach IP-Adressen sucht.


### Aufgabe 2 – Deaktivieren des Features „An Kindle senden“, das DLP-Richtlinien umgeht

Holly Dickson, der Microsoft 365-Admin von Adatum, hat kürzlich in Microsoft 365 über ein Feature zum **Senden an Kindle** erfahren, mit dem Sie Microsoft Word-Dokumente in nur wenigen Minuten direkt an Ihre Kindle-Bibliothek senden können. Eine übertragene Datei kann wie ein Kindle-Buch mit anpassbaren Schriftgraden oder wie ein gedrucktes Dokument mit festen Layouts erscheinen, um ihre Seitenentwurfsformatierung beizubehalten. 

Das Problem mit diesem Feature besteht darin, dass DLP-Richtlinien die Word-Dateifreigabe nicht auf Kindle berücksichtigen, wodurch die DLP-Steuerelemente umgangen werden. Da Adatum dieses Feature zum **Senden an Kindle** nicht verwenden wird, möchte Holly sie deaktivieren, um zu verhindern, dass Benutzende die DLP-Richtlinien des Unternehmens umgehen. 

Um diese Einstellung zu deaktivieren, müssen Sie im Microsoft Intune Admin Center eine Richtlinie für Office-Apps erstellen. In der von Ihnen erstellten Richtlinie fügen Sie die Einstellung **„An Kindle senden“ deaktivieren** hinzu und aktivieren dann diese Einstellung. Wenn Sie diese Einstellung in der Richtlinie aktivieren, wird das Feature **An Kindle senden** deaktiviert, sobald Sie die Richtlinie erstellt haben. Ab diesem Zeitpunkt können die Benutzenden keine Word-Dokumente mehr an ihre Kindle-Bibliothek senden.

**Hinweis:** Dieses Problem ist etwas, das Sie in Ihren realen Microsoft 365-Bereitstellungen berücksichtigen sollten. Weitere Informationen zu dem **An Kindle senden**-Feature finden Sie unter https://support.microsoft.com/office/send-to-kindle-a53d880d-9952-4bf1-abc5-6bce8db5a273.

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson** angemeldet sein. 

2. Suchen Sie in Ihrem Edge-Browser die Registerkarte **Microsoft 365 Admin Center**. Wählen Sie im Navigationsbereich des Microsoft 365 Admin Centers unter der Gruppe **Admin Center** die Option **Endpoint Manager** aus.

3. Wählen Sie im **Microsoft Intune Admin Center**, das sich in einer neuen Registerkarte öffnet, im Navigationsbereich **Apps**.

4. Wählen Sie auf der Seite **Apps | Übersicht** im mittleren Navigationsbereich unter dem Abschnitt **Richtlinie** die Option **Richtlinien für Office-Apps**.

5. Wählen Sie auf der Seite **Apps | Richtlinien für Office- Apps** die Schaltfläche **Erstellen**. Dadurch wird der Assistent zum Erstellen einer neuen Richtlinie gestartet. In den verbleibenden Schritten werden Sie die Einstellung **„An Kindle senden“ deaktivieren** innerhalb dieser Richtlinie aktivieren.

6. Geben Sie auf der Seite **Mit den Grundlagen beginnen** in das Feld **Name** die Einstellung **„An Kindle senden“ deaktivieren** ein und wählen Sie dann **Weiter**.

7. Wählen Sie auf der Seite **Bereich auswählen** die Option **Diese Richtlinienkonfiguration gilt für alle Benutzer** und wählen Sie dann **Weiter**.

8. Beachten Sie auf der Seite **Einstellungen festlegen** die Metriken, die über der Liste der Einstellungen angezeigt werden. Es gibt mehr als 2200 Office-App-Einstellungen für Ihre Mandantenkonfiguration. Um diese Einstellung schnell festzulegen, geben Sie **Kindle** in das **Suchfeld** ein und drücken Sie dann **Eingabe**. Dadurch sollten alle Richtlinien mit **Kindle** im Richtliniennamen angezeigt werden.

9. Wie Sie sehen können, gibt es nur eine Kindle-Einstellung, nämlich **„An Kindle senden“ deaktivieren**. Wählen Sie diese Einstellung, um den Bereich **„An Kindle senden“ deaktivieren** zu öffnen.

10. Im Bereich **„An Kindle senden“ deaktivieren** werden die Plaforms und Anwendungen angezeigt, für die diese Einstellung gilt. Wählen Sie unter der Beschreibung die Option **Mehr anzeigen** aus. Lesen Sie die vollständige Beschreibung dieser Einstellung.

11. Wählen Sie den Dropdownpfeil im Feld **Konfigurationseinstellung**. Wählen Sie im angezeigten Dropdownmenü **Aktiviert** aus.

12. Wählen Sie am unteren Rand des Fensters die Schaltfläche **Anwenden**.

13. Auf der Seite **Einstellungen konfigurieren** sollte die Richtlinie **„An Kindle senden“ deaktivieren** erscheinen, und ihr **Status** sollte auf **Konfiguriert** festgelegt sein. Wählen Sie **Weiter** aus.

14. Wählen Sie auf der Seite **Konfiguration prüfen und erstellen** die Schaltfläche **Erstellen**. 

15. Wählen Sie auf der Seite **Richtlinienkonfiguration erstellt** die Option **Fertig**.
 
16. Lassen Sie Ihren Edge-Browser geöffnet. Schließen Sie keine der Registerkarten.


Indem Sie diese Einstellung **„An Kindle senden“ deaktivieren** in der neuen Richtlinie, die Sie gerade erstellt haben, aktivieren, haben Sie die Funktion **An Kindle senden** deaktiviert. Damit wird verhindert, dass die Benutzenden von Adatum Word-Dokumente an ihre Kindle-Bibliothek senden, wodurch die DLP-Richtlinien des Unternehmens umgangen werden.


# Weiter zu Lab 3 – Übung 2 
