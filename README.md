# Threads-Bankanwendung
Bankkontoverwaltung durch Threads
Problem, falls der Zugrif der Überweisungsthreads  auf das Konto nicht synchronisiert stattfindet:
Die Überweisungen u1 bis u3 werden parallel ausgeführt. Dabei kann es passieren, dass mehrere
Überweisungen erst nacheinander den aktuellen Kontostand lesen, dann nacheinander den Betrag
hinzuaddieren und anschließend nacheinander den neuen Kontostand schreiben. Im schlimmsten Falle
hat das Konto danach einen Kontostand von 10.
Die Lösung mit synchronisiertem Überweisungsthreads über dem Konto sichert zu, dass für jedes Konto nur eine Überweisung gleichzeitig den
kritischen Codeabschnitt ausführt.
Die run-Methode mit einem synchronized-Schlüsselwort zu versehen würde auch nicht helfen, da dies  einem synchronized (this) { … } entspräche und entsprechend nur zusichern würde , dass pro Überweisung der kritische Codeblock nur einmal ausgeführt wird. Den Konflikt der Überweisungen untereinander löst diese Änderung nicht.
