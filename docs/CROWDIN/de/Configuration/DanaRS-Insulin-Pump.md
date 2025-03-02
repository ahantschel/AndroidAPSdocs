# DanaRS und Dana-i Pumpe

*Diese Anleitung beschreibt die Einrichtung der App und Deiner Pumpe, wenn du eine Dana RS (ab 2017) oder die neuere Dana-i verwendest. Gehe zu [DanaR Insulinpumpe](./DanaR-Insulin-Pump) wenn du die Original DanaR benutzt.*

**Die neue Dana RS Firmware v3 wird ab AAPS-Version 2.7 unterstützt.**

**Die neue Dana-i kann ab AndroidAPS Version 3.0 verwendet werden.**

* Bei der DanaRS und Dana-i wird das Basalprofil "BASAL A" von AAPS verwendet. Eventuell in der Pumpe vorhandene Einträge in diesem Profil werden überschrieben.

(DanaRS-Insulin-Pump-pairing-pump)=

## Pumpe verbinden

* Klicke auf dem AndroidAPS Startbildschirm oben links auf das Hamburger Menü und wähle den Konfigurations-Generator aus.
* Wähle 'Dana-i/RS' im Abschnitt Pumpe.
* Über das Zahnrad erreichst Du die Pumpeneinstellungen direkt oder Du wählst den Weg über den Startbildschirm.
    
    ![AAPS Konfigurations-Generator Dana-i/RS](../images/DanaRS_i_ConfigB.png)

* Gehe zum 'DANA-i/RS' Tab.

* Wähle das Einstellungsmenü. Klicke dazu auf die drei Punkte rechts oben. 
* Wähle die 'Dana-i/RS Einstellungen'.
* Klicke auf "Ausgewählte Pumpe"
* Im Fenster zum Kopplungsprozess ('Pairing') klicke auf den Eintrag Deiner Pumpe.
    
    ![Dana-i/RS mit AndroidAPS verbinden](../images/DanaRS_i_Pairing.png)

* **Du musst die Verbindung auf der Pumpe bestätigen!** Das funktioniert genau gleich wie Du es von der Verbindung Deines Smartphones mit anderen Bluetooth-Geräten wie z.B. Bluetooth-Kopfhörern kennst.
    
    ![Bestätigung der Verbindung auf der Dana RS](../images/DanaRS_Pairing.png)

* Der Kopplungsprozess unterscheidet sich abhängig vom Pumpentyp und Firmware:
    
    * Für DanaRS v1 wähle das Pumpenpasswort in den Einstellungen und gibt Dein Passwort ein.
    * Für DanaRS v3 musst Du zwei Zahlenfolgen und Buchstaben in den AndroidAPS-Paarungsdialog eingeben, die auf der Pumpe angezeigt werden.
    * Für Dana-i wird der Standard-Android-Kopplungsdialog angezeigt und Du musst eine 6-stellige Nummer, die im Pumpendisplay angezeigt wird, eingeben.

* Klicke auf "Bolus-Geschwindigkeit" um die gewünschte Abgabegeschwindigkeit (12 s/1 IE, 30 s/1 IE oder 60 s/1 IE) einzustellen.

* Stelle im Arztmenü auf der Pumpe (siehe Bedienungsanleitung der DanaRS) die BASALschritte auf 0,01 IE/h.
* Stelle im Arztmenü auf der Pumpe (siehe Bedienungsanleitung der DanaRS) die Bolus-Schritte auf 0,05 IE/h.
* Aktiviere verzögerten Bolus in der Pumpe.

(DanaRS-Insulin-Pump-default-password)=

### Standard-Passwort

* Für die DanaRS mit Firmware v1 und v2 ist das Standard-Passwort 1234.
* Für die DanaRS mit Firmware v3 oder Dana-i wird das Standard-Passwort durch die Kombination von Produktionsmonat und Produktionsdatum gebildet (z.B. Monat 01 und Tag 24).
    
    * Öffne auf der Pumpe das Hauptmenü > Prüfen > Geräte Info. 
    * Nummer 3 ist das Produktionsdatum. 
    * Bei DanaRS v3 und Dana-i wird dieses Passwort nur verwendet, um die Tasten der Pumpe zu sperren. Es wird nicht für die Kommunikation verwendet und muss daher nicht in AndroidAPS eingegeben werden.

(DanaRS-Insulin-Pump-change-password-on-pump)=

## Passwort auf Pumpe ändern

* Auf der Pumpe Taste OK drücken.
* Im Hauptmenü "EINSTELLUNGEN" wählen. (Dazu nach rechts scrollen indem Du mehrfach den Pfeiltaste drückst.)
    
    ![DanaRS Hauptmenü](../images/DanaRSPW_01_MainMenu.png)

* Wähle im Untermenü "ANWENDER MENÜ".
    
    ![DanaRS Menü Optionen](../images/DanaRSPW_02_OptionMenu.png)

* Scrolle mit der Pfeiltaste nach unten zu "11. Passwort".
    
    ![DanaRS 11. Passwort](../images/DanaRSPW_03_11PW.png)

* Drücke OK, um das bisherige Passwort einzugeben.

* Enter **old password** (Default password see [above](DanaRS-Insulin-Pump-default-password)) and press OK
    
    ![DanaRS altes Kennwort eingeben](../images/DanaRSPW_04_11PWenter.png)

* Wenn hier das falsche Passwort eingegeben wird, gibt es keine Fehlermeldung!

* Lege ein **neues Passwort** fest (Ändere die Ziffern mit den + & - Buttons / gehe mit dem Pfeil-Button nach rechts).
    
    ![DanaRS neues Passwort](../images/DanaRSPW_05_PWnew.png)

* Bestätige mit der OK-Taste.

* Speichere durch erneutes Drücken der OK-Taste.
    
    ![DanaRS Neues Kennwort speichern](../images/DanaRSPW_06_PWnewSave.png)

* Scrolle nach unten zu "14. EXIT" und drücke die OK-Taste.
    
    ![DanaRS Exit](../images/DanaRSPW_07_Exit.png)

(DanaRS-Insulin-Pump-dana-rs-specific-errors)=

## Dana RS spezifische Fehler

### Fehler bei der Insulinabgabe

In case the connection between AAPS and Dana RS is lost during bolus insulin delivery (i.e. you walk away from phone while Dana RS is pumping insulin) you will see the following message and hear an alarm sound.

![Alarm insulin delivery](../images/DanaRS_Error_bolus.png)

* In den meisten Fällen handelt es sich nur um ein Kommunikationsproblem und es wurde tatsächlich die korrekte Insulinmenge abgegeben.
* Prüfe in der Historie der Dana RS (entweder direkt in der Pumpe oder über den Dana Tab > Pumpen-Speicher > Boli), ob die korrekte Bolusmenge abgegeben wurde.
* Delete error entry in [treatments tab](Screenshots-carb-correction) if you wish.
* Die tatsächlich abgegebene Insulinmenge wird bei der nächsten Verbindung zwischen AAPS und Dana RS ausgelesen. Um eine Verbindung manuell herzustellen, drücke das Bluetooth Icon auf dem Dana Tab oder warte einfach auf die nächste Verbindung.

## Wichtiger Hinweis beim Wechsel des Smartphones

When switching to a new phone the following steps are necessary:

* [Export settings](ExportImportSettings-export-settings) on your old phone
* Übertrage die Einstellungen vom alten auf das neue Smartphone.

### DanaRS v1

* Verbinde die Dana RS **manuell** mit dem neuen Smartphone.
* Da die Verbindungseinstellungen zusammen mit den anderen Einstellungen in AAPS importiert werden, "kennt" AAPS deine Pumpe bereits und startet daher keinen Bluetooth-Scan. Daher müssen das neue Smartphone und die Pumpe manuell verbunden werden.
* Installiere AndroidAPS auf dem neuen Smartphone.
* [Import settings](ExportImportSettings-import-settings) on your new phone

### DanaRS v3, Dana-i

* Start pairing procedure like decribed [above](DanaRS-Insulin-Pump-pairing-pump).
* Manchmal kann es notwendig sein, die Kopplung von AndroidAPS zu löschen, indem Du auf dem Dana-i/RS Tab auf das Bluetooth-Symbol drückst.

## Mit der Dana RS Pumpe über Zeitzonen hinweg reisen

For information on traveling across time zones see section [Timezone traveling with pumps](Timezone-traveling-danarv2-danars).