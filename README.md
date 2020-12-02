# Git Guide für Teddymaus

Bei git hast du immer ein lokales Repository (auf deinem Computer) und ein online Repository (bspw. GitHub).<br>
Der Vorteil vom online Repository ist, dass mehrere Personen mit dem Code arbeiten können.<br>
Dafür holt man sich zu Beginn einen Klon vom online Stand auf den Rechner: ```git clone <internet-adresse-des-repositories>```.<br>
Wenn du dein lokales Repository darüber informieren möchte, was online so passiert ist, verwendet man ```git fetch```.<br>
Dabei wird aber dein eigenes lokales Repository nicht verändert - du holst dir nur Informationen. Erst mit ```git pull``` holst du dir den Code.<br>
Wenn du einen neuen lokalen Branch erstellen möchtest, verwendest du ```git checkout -b <branch-name>```.<br>
Deine lokalen Daten kannst du auf eine "stage" bringen. Du fügst Dateien auf eine "stage" mithilfe von ```git add <deine-datei>``` hinzu.<br>
Wenn du deine lokale Stage sichern möchtest, dann kannst du ```git commit -m "hier beschreiben was du gemacht hast``` eingeben.<br>
Nachdem du deinen Code geschrieben hast und mit anderen teilen möchtest, pushst du ihn auf das online Repository (bspw. GitHub oder GitLab) mithilfe von ```git push --set-upstream origin <branch-name>```<br>
Die Option ```--set-upstream``` ist nicht notwendig, wenn der Upstream bereits bekannt ist. Dann kannst du ```git push``` schreiben.<br>

# Übersicht

### Mit Repositories arbeiten
* Lokales Repository erstellen: ```git init```
* Online Repository erstellen. Graphisches Interface vom online Repository verwenden
* Lokales Repository mit online Repository verknüpfen (bevor du das machst, ist es sinnvoll Code zu schreiben oder Dateien hinzuzufügen! Siehe unten, wie man Dateien <b>staget</b> und <b>committet</b>): ```git remote add origin <internet-adresse-des-repositories>```
* Du kannst ein online Repository auch klonen: ```git clone <internet-adresse-des-repositories>```

### Informationen holen
* Informationen holen: ```git fetch```
* Lokalen Stand aktualisieren: ```git pull```
* <b>Status abfragen!</b> Super wichtig!: ```git status```

### Mit Branches arbeiten
* Lokalen Branch erstellen: ```git checkout -b <branch-name>```
* Zu Branch wechseln (bestimmte online Branches muss man erst über ```git fetch``` holen): ```git checkout <branch-name>```
* Lokalen Branch löschen: ```git branch -d <branch-name>```
* Online Branch löschen (hier wurde ```origin```als "remote name" verwendet. Ist Standard!): ```git push -d origin <branch-name>```

### Zwei Branches mergen
1. Auf den Branch wechseln, der aktualisiert werden soll.
2. Es bietet sich hier an, dass du das graphische Interface von bspw. IntelliJ oder PyCharm verwendest.
3. Dafür klickst du rechts unten auf ```git``` und auf den Branch, von dem du dir den Code holen möchtest. Die Option "merge into current" sorgt dafür, dass du den Code vom ausgewählten Branch in deinen jetzigen mergest. Falls du den Branch nicht finden solltest, hol dir die Informationen vom online Repository über ```git fetch```
4. Es öffnet sich eine graphische Oberfläche mit den Dateien, die sich unterscheiden und nicht automatisch mergen lassen.
5. Auf die Dateien klicken und mit den Symbolen x und >> den jeweiligen Code akzeptieren oder ablehnen
* Falls ein <b>merge Konflikt</b> in der Konsole auftreten sollte und du das abbrechen möchtest: ```git merge --abort```

### Dateien sichern
* Dateien stagen: ```git add <deine-datei>```<br> oder alle Dateien stagen: ```git add -A```
* Bestimmte Dateien bspw. alle ```.py``` Dateien stagen (einfach einen regulären Ausdruck verwenden): ```git add *.py```
* Dateien lokal sichern: ```git commit``` für Eingabefenster oder ```git commit -m "hier die commit Nachricht eingeben``` mit Nachricht (ist einfacher)
* Lokalen Stand auf das online Repository sichern: ```git push```<br> oder ```git push --set-upstream origin <branch-name>```, falls git nicht weiß auf welchen online Branch es pushen soll
* Lokalen Stand auf den letzten commit zurücksetzen: ```git reset --hard```

## Wichtiges!

Reihenfolge beim hinzufügen:
* Code schreiben / Dateien hinzufügen
* Dateien stagen
* committen
* pushen

Reihenfolge beim holen:
* Code fertig schreiben
* Dateien stagen
* Dateien committen
* pullen
* falls <b>merge Konflikte</b> auftreten, abbrechen (siehe oben, wie man das abbricht) und das graphische Interface verwenden. Man pullt dann über den Pfeil, der nach unten zeigt!
* Nach lösen evtl. merge Konflikte, pushen

<b>Manchmal sieht es so aus, als wäre nichts passiert!. Einfach in den Code klicken -> dadurch aktualisiert die IDE (IntelliJ / PyCharm / ...) das, was git gemacht hat</b>