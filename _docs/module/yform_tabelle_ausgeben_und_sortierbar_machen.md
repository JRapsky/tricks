Für ein kleines Projekt habe ich mit Yform eine neue Tabelle mit verschiedenen Produkten erstellt. Für jedes Produkt wurden
verschiedene Eigenschaften hinterlegt. Ziel war es ein Modul zu schaffen, mit dem sich alle Produkte tabellarisch darstellen
lassen. Außerdem sollten die Produkte auch nach ihren Eigenschaften sortierbar sein.

Die fertige Ausgabe meines Modul sieht so aus:

//FutterDB = Name der Tabelle
//Hersteller Sorte Menge Rohprotein... sind die Spaltennamen
$list = rex_list::factory('SELECT Hersteller,Sorte,Menge,Rohprotein,Rohfett,Rohfaser,Calcium,Phosphor FROM FutterDB');

//mit setColumnLabel lässt sich die Ausgabe des Spaltenkopfes beeinflussen
$list->setColumnLabel('Menge', 'Menge Kg');	
$list->setColumnLabel('Rohprotein', '% Rohprotein');
$list->setColumnLabel('Rohfett', '% Rohfett');
$list->setColumnLabel('Rohasche', '% Rohasche');
$list->setColumnLabel('Rohfaser', '% Rohfaser');
$list->setColumnLabel('Calcium', '% Calcium');
$list->setColumnLabel('Phosphor', '% Phosphor');

//die beiden folgenden Zeilen sind notwendig für die Sortierbarkeit, er dient ihrem Artikel zur Orientierung
$list->addParam('article_id', 'REX_ARTICLE_ID');
$list->addParam('clang', 'REX_CLANG_ID');

//ab hier kann man die Spaltenköpfe eintragen, die später sortierbar sein sollen
$list->setColumnSortable('Hersteller');
$list->setColumnSortable('Rohprotein');
$list->setColumnSortable('Rohfett');
$list->setColumnSortable('Rohasche');
$list->setColumnSortable('Rohfaser');
$list->setColumnSortable('Calcium');
$list->setColumnSortable('Phosphor');

//die Anweisung für die Ausgabe im Frontend
$list->show();
