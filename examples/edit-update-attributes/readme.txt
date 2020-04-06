In diesem Beispiel soll kurz gezeigt werden, wie ein einfaches Eingabeformular
zum Updaten von bestehenden Datenstätzen realisiert werden kann.

Achtung: DataLinq dient nur zum Erfassen von Sachdaten (keine Geometrie)

Hinweis: Auf die gleiche Weise kann theoretisch auch eine Maske zum Erstellen
von Datenstätzen implementiert werden. Der Unterschied ist hier nur das SQL-Statement (INSERT statt UPDATE) 

1. Endpoint auf Datenbank anlegen (zB update-data): 
Der Datenbankuser im ConnectionString muss schreibreichte auf die entsprechenden Datenbank Tabellen haben

2. Eine Query für die Eingabemaske erstellen (zB select-record):
Die Eingabemaske sollte später mit der ensprechenden Id des Datansatzes aufgerufen werden. Als Url-Paramweter sollte hier &id=... dienen.
(https://..../datalinq/resport/@update-data@select-record@update-record-form?id=123)

SELECT
    OBJECTID
    ,FIELD1
    ,FIELD2
    ,FIELD3
    ,FIELD4
FROM
MY_TABLE_TO_UPDATE

where OBJECTID = @id

3. Eine Query für den Update anlegen (zB update-record):

update
	MY_TABLE_TO_UPDATE
set
	FIELD1 = @FIELD1
    ,FIELD2 = @FIELD2
    ,FIELD3 = @FIELD3
    ,FIELD4 = @FIELD4
where
	OBJECTID = @OBJECTID

4. unter der Query aus Punkt 2 einen View für die Editmaske anlegen (zB. update-record-form)
(siehe File update-record-form.cshtml)


