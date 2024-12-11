# Lernpfad 1, Lab 3, Übung 2: Testen der DLP-Richtlinie

Holly Dickson befindet sich nun an dem Punkt in ihrem Pilotprojekt, an dem sie die DLP-Richtlinie im Zusammenhang mit E-Mails testen möchte, die vertrauliche Informationen enthalten, die Sie in der vorherigen Übung erstellt haben. 

**Hinweis:** In der Vergangenheit sind gelegentlich Probleme aufgetreten, bei denen DLP-Richtlinien und Richtlinientipps in dieser Lab-Übung nicht wie erwartet funktioniert haben. Dies liegt an Drosselungsproblemen, die manchmal zwischen unserer VM-Lab-Umgebung und dem Microsoft 365-Testmandanten auftreten. Dies entspricht nicht der normalen Erfahrung in Microsoft 365-Produktionsumgebungen. Es ist auch kein Hinweis auf die normale Trainingserfahrung. Wir entschuldigen uns, falls Sie während dieses Labs auf dieses Problem stoßen.

### Aufgabe 1: Testen der ersten DLP-Richtlinienregel

In der vorherigen Übung haben Sie eine benutzerdefinierte DLP-Richtlinie erstellt, die E-Mails nach vertraulichen Informationen im Zusammenhang mit IP-Adressen in Ihrem Adatum-Mandanten durchsucht. Diese Richtlinie umfasste zwei Regeln: eine, die E-Mails mit einer einzelnen IP-Adresse überprüfte, und eine weitere, die E-Mails mit zwei oder mehr IP-Adressen überprüfte. 

In dieser Aufgabe senden Sie eine E-Mail von Holly Dickson an Lynne Robbins, die die erste Regel (einzelne IP-Adresse) testet. Wenn diese Regel ausgelöst wird, wird ein E-Mail-Richtlinientipp im Outlook-Postfach des Absenders bzw. der Absenderin angezeigt, der ihn oder sie darüber informiert, dass die E-Mail vertrauliche Daten enthält. Diese Person erhält auch eine E-Mail-Benachrichtigung, die E-Mail wird jedoch weiterhin an die Empfangenden gesendet.

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson**angemeldet sein. 

2. Sie senden jetzt eine E-Mail von Holly an Lynne Robbins, und Sie fügen eine IP-Adresse in den Textkörper der E-Mail ein. <br/>

    Wählen Sie in **Microsoft Edge** die Registerkarte **Startseite | Microsoft 365** aus und wählen Sie dann das Symbol **Outlook** in der Spalte mit den App-Symbolen auf der linken Seite des Bildschirms aus. Wenn Outlook im Web geöffnet wird, sollten Sie automatisch als Holly Dickson angemeldet sein.  <br/>

    **Hinweis:** Wenn **Outlook im Web** bereits geöffnet war, überprüfen Sie, ob Sie als **Holly** angemeldet sind, indem Sie das Benutzersymbol in der oberen rechten Ecke (den **HD-Kreis**) überprüfen. Wenn Outlook für ein anderes Benutzerkonto geöffnet war, schließen Sie die Registerkarte und wiederholen Sie die Anweisungen in diesem Schritt, um Outlook im Web für Holly zu öffnen.

3. Wählen Sie in der oberen linken Ecke des Bildschirms **Neue E-Mail** aus. 

4. Geben Sie im Nachrichtenbereich, der auf der rechten Seite des Bildschirms angezeigt wird, die folgenden Informationen ein:

    - An: Geben Sie **Lynne** ein und wählen Sie dann **Lynne Robbins** aus der angezeigten Liste der Benutzenden aus.

    - Betreff hinzufügen: **DLP-Richtlinientest 1**

    - Nachrichtenbereich: **Hey Lynne, Ich werde diese IP-Adresse konfigurieren: 192.168.0.1**

    **Hinweis:** Wenn Sie diese E-Mail mit sensiblen Daten (in diesem Fall eine IP-Adresse) verfassen, wird die zuvor von Ihnen erstellte IP-Adressrichtlinie und insbesondere die Regel für einzelne IP-Adressen ausgelöst. Daher sollte ein **Richtlinientipp** angezeigt werden, der angibt, dass die E-Mail-Nachricht gegen eine Organisationsrichtlinie verstößt. Sie ignorieren diesen Richtlinientipp und senden die E-Mail trotzdem, um den Rest der DLP-Richtlinie zu testen, wodurch eine Benachrichtigungs-E-Mail an Holly gesendet wird.

5. Sobald der Richtlinientipp angezeigt wird, wählen Sie **Senden.**

6. Wählen Sie den Ordner **Gesendete Elemente** von Holly, um zu überprüfen, ob die E-Mail gesendet wurde.

7. Wählen Sie den Ordner **Posteingang** von Holly aus. Holly sollte eine E-Mail von **Microsoft Outlook** mit dem Betreff erhalten: **Benachrichtigung: DLP-Richtlinientest 1**. Wählen Sie diese E-Mail aus, und überprüfen Sie deren Inhalt. 

8. Wechseln Sie zu **LON-CL2**. 

9. Wenn Sie sich bei der VM anmelden müssen, sollte standardmäßig das lokale Konto **LON-CL2\admin** erscheinen. Geben Sie also **Pa55w.rd** in das Feld **Kennwort** ein, um sich anzumelden. 

10. Wählen Sie in der Taskleiste das Symbol für den **Edge**-Browser.

11. Geben Sie im Edge-Browser die folgende URL ein: **https://outlook.office365.com**

12. Wählen Sie im Fenster **Konto auswählen** das Konto von Lynne Robbins (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**, wobei „xxxxxZZZZZZ“ das von Ihrem Lab-Hostinganbieter bereitgestellte Mandant-Präfix ist). Geben Sie im Fenster **Kennwort eingeben** das neue Benutzerkennwort ein, das Sie Lynnes Konto zugewiesen haben, und wählen Sie dann **Einloggen**. 

13. Aktivieren Sie im Fenster **Angemeldet bleiben** das Kontrollkästchen **Nicht mehr anzeigen** und wählen Sie **Ja**.

14. Überprüfen Sie im Posteingang von Lynne, ob sie die E-Mail von Holly Dickson erhalten hat, die die folgende Betreffzeile hat: **DLP-Richtlinientest 1**. Wählen Sie die Nachricht aus, um zu überprüfen, ob der Inhalt, der die IP-Adresse enthält, nicht entfernt wurde. 

15. Lassen Sie die Outlook-Registerkarte im Edge-Browser für die nächste Aufgabe geöffnet.

16. Wechseln Sie zurück zu **LON-CL1**.

    
### Aufgabe 2: Testen der zweiten DLP-Richtlinienregel

In der vorherigen Übung haben Sie eine benutzerdefinierte DLP-Richtlinie erstellt, die E-Mails nach vertraulichen Informationen im Zusammenhang mit IP-Adressen in Ihrem Adatum-Mandanten durchsucht. Diese Richtlinie umfasste zwei Regeln: eine, die E-Mails mit einer einzelnen IP-Adresse überprüfte, und eine weitere, die E-Mails mit zwei oder mehr IP-Adressen überprüfte. 
    
In dieser Aufgabe senden Sie eine E-Mail von Holly Dickson an Lynne Robbins, die die zweite Regel testet (mehrere IP-Adressen). Wenn diese Regel ausgelöst wird, wird ein E-Mail-Richtlinientipp im Outlook-Postfach des Absenders bzw. der Absenderin angezeigt, der ihn oder sie darüber informiert, dass die E-Mail vertrauliche Daten enthält. Die E-Mail wird blockiert, aber der Absender bzw. die Absenderin kann die blockierte E-Mail außer Kraft setzen und das Senden zulassen.  

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson**angemeldet sein. 
    
2. Sie senden nun eine zweite Nachricht von Holly an Lynne, die mehrere IP-Adressen enthält. Wiederholen Sie den Vorgang wie zuvor, um eine E-Mail an Lynne Robbins mit den folgenden Informationen zu erstellen: 

    - Betreff hinzufügen: **DLP-Richtlinientest 2**

    - Nachrichtenbereich: **Hey Lynne, Ich werde die folgenden IP-Adressen testen: 192.168.0.1 und 172.16.0.1**

    **Hinweis:** Wenn Sie diese E-Mail mit sensiblen Daten (in diesem Fall mehrere IP-Adressen) verfassen, wird sie die IP-Adressen-Richtlinie auslösen, die Sie zuvor erstellt haben, und insbesondere die Regel für mehrere IP-Adressen. Daher sollte ein **Richtlinientipp** angezeigt werden, der angibt, dass die E-Mail-Nachricht gegen eine Organisationsrichtlinie verstößt. Sie ignorieren diesen Richtlinientipp und senden die E-Mail trotzdem, um den Rest der DLP-Richtlinie zu testen, wodurch die E-Mail blockiert wird. Sobald Sie die E-Mail-Blockierung getestet haben, heben Sie die Blockierung auf, indem Sie eine geschäftliche Begründung für den Versand dieser sensiblen Daten eingeben, und versuchen Sie dann erneut, die E-Mail zu versenden.

3. Sobald der Richtlinientipp angezeigt wird, wählen Sie **Senden**. Sie sollten sofort ein Dialogfeld **Senden blockiert** erhalten, das darauf hinweist, dass die Nachricht einen oder mehrere Empfangende enthält, die nicht berechtigt sind, sensible Informationen zu empfangen. Wählen Sie **OK** aus. <br/>

    **Hinweis:** Normalerweise würden Sie die Blockierung vor dem Senden aufheben, aber in diesem Fall möchten wir, dass Sie die Blockierung erleben, um zu sehen, wie sie funktioniert. In den nächsten Schritten werden Sie die Blockierung aufheben und versuchen, die E-Mail erneut zu senden.

4. Wählen Sie den Ordner **Gesendete Elemente** von Holly aus, um zu überprüfen, ob die E-Mail nicht gesendet wurde.

5. Wählen Sie den Ordner **Posteingang** von Holly aus. Beachten Sie, dass die E-Mail-Nachricht nicht mehr angezeigt wird. Wählen Sie den Ordner **Entwürfe** von Holly aus, der eine Kopie der E-Mail enthält. Wählen Sie die E-Mail aus.

6. Um diese E-Mail zu senden, müssen Sie die Blockierung aufheben, BEVOR Sie auf die Schaltfläche **Senden** klicken. Um die Blockierung aufzuheben, wählen Sie in dem oben in der Nachricht angezeigten Richtlinientipp die Option **Details anzeigen** aus.

7. Wählen Sie in der Detailmeldung, die im Richtlinientipp angezeigt wird, die Option **Überschreiben** aus.

8. Im angezeigten Dialogfeld ist die Option **Ich habe eine geschäftliche Begründung** standardmäßig ausgewählt. Lassen Sie diese Option aktiviert und geben Sie **Lynne muss über die IP-Adressen, die ich teste, informiert werden** in das Feld **Erklärung hier eingeben** ein. Wählen Sie **Überschreiben**. <br/>

    Beachten Sie, dass sich die Meldung mit dem Richtlinientipp geändert hat, um anzuzeigen, dass Sie sich dafür entschieden haben, die Nachricht zu senden, obwohl sie anscheinend vertrauliche Informationen enthält.

9. Wählen Sie den Ordner **Gesendete Elemente** von Holly, um zu überprüfen, ob die E-Mail gesendet wurde.

10. Wählen Sie den Ordner **Posteingang** von Holly aus. Holly sollte eine E-Mail von **Microsoft Outlook** mit dem Betreff **Benachrichtigung: DLP-Richtlinientest 2** erhalten. Wählen Sie diese E-Mail aus, und überprüfen Sie deren Inhalt.
    
11. Wechseln Sie zu **LON-CL2**. 

12. Sie sollten weiterhin in **Outlook im Web** auf der LON-CL2-VM als **Lynne Robbins** angemeldet sein. **Im Edge-Browser** sollte das Postfach von Lynne weiterhin in **Outlook im Web** geöffnet sein, wenn Sie es zuletzt in der vorherigen Aufgabe verwendet haben.

13. Überprüfen Sie im Posteingang von Lynne, ob sie die E-Mail von Holly Dickson erhalten hat, die die folgende Betreffzeile hat: **DLP-Richtlinientest 2**. Wählen Sie die Nachricht aus, um zu überprüfen, ob der Inhalt, der die IP-Adressen enthält, nicht entfernt wurde. 

14. Lassen Sie die Outlook-Registerkarte im Edge-Browser für die nächste Aufgabe geöffnet.

15. Wechseln Sie zurück zu **LON-CL1**.

    
# Ende von Lab 3
