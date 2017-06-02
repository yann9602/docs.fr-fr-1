---
title: "Recherche de lignes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Recherche de lignes
Vous pouvez rechercher des lignes en fonction des valeurs de leur clé de tri en utilisant les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de l'objet <xref:System.Data.DataView>.  Le respect ou le non\-respect de la casse des valeurs de recherche des méthodes **Find** et **FindRows** est déterminé par la propriété **CaseSensitive** de l'objet <xref:System.Data.DataTable> sous\-jacent.  Pour qu'un résultat soit retourné, les valeurs de recherche doivent correspondre aux valeurs des clés de tri existantes dans leur intégralité.  
  
 La méthode **Find** retourne un entier avec l'index de l'objet <xref:System.Data.DataRowView> qui correspond aux critères de recherche.  Si plusieurs lignes correspondent aux critères de recherche, seul l'index du premier **DataRowView** correspondant est retourné.  Si aucune correspondance n'est trouvée, **Find** retourne \-1.  
  
 Pour retourner des résultats de recherche qui correspondent à plusieurs lignes, utilisez la méthode **FindRows**.  La méthode **FindRows** fonctionne de la même manière que **Find**, à cette exception qu'elle retourne un tableau **DataRowView** faisant référence à toutes les lignes du **DataView** qui présentent une correspondance.  Si aucune correspondance n'est trouvée, le tableau **DataRowView** sera vide.  
  
 Pour utiliser les méthodes **Find** ou **FindRows**, vous devez spécifier un ordre de tri soit en définissant pour **ApplyDefaultSort** la valeur **true**, soit en utilisant la propriété **Sort**.  Si aucun ordre de tri n'est spécifié, une exception est levée.  
  
 Les méthodes **Find** et **FindRows** acceptent comme entrée un tableau de valeurs dont la longueur correspond au nombre de colonnes incluses dans l'ordre de tri.  Si un tri doit s'effectuer sur une seule colonne, vous pouvez passer une seule valeur.  Pour les ordres de tri incluant plusieurs colonnes, vous passez un tableau d'objets.  Notez que pour un tri sur plusieurs colonnes, les valeurs figurant dans le tableau d'objets doivent correspondre à l'ordre des colonnes spécifié dans la propriété **Sort** du **DataView**.  
  
 L'exemple de code suivant illustre la méthode **Find** appelée sur un **DataView** avec un ordre de tri défini sur une seule colonne.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Si votre propriété **Sort** spécifie plusieurs colonnes, vous devez passer un tableau d'objets avec les valeurs de recherche pour chaque colonne incluse dans l'ordre spécifié par la propriété **Sort**, comme dans l'exemple de code suivant.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)