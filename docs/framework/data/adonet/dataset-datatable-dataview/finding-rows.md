---
title: Recherche de lignes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9ede2dbf0718a4ca1d8025af3ce60c256afc867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="finding-rows"></a>Recherche de lignes
Vous pouvez rechercher des lignes en fonction des valeurs de leur clé de tri en utilisant les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de l'objet <xref:System.Data.DataView>. Le respect de la recherche des valeurs dans le **trouver** et **FindRows** méthodes est déterminé par le **CaseSensitive** propriété de l’objet sous-jacent <xref:System.Data.DataTable>. Pour qu'un résultat soit retourné, les valeurs de recherche doivent correspondre aux valeurs des clés de tri existantes dans leur intégralité.  
  
 Le **trouver** méthode retourne un entier avec l’index de la <xref:System.Data.DataRowView> qui correspond aux critères de recherche. Si plusieurs lignes correspond aux critères de recherche, seul l’index du premier correspondants **DataRowView** est retourné. Si aucune correspondance n’est trouvée, **trouver** retourne -1.  
  
 Pour retourner les résultats de recherche qui correspondent à plusieurs lignes, utilisez la **FindRows** (méthode). **FindRows** fonctionne exactement comme le **trouver** (méthode), à ceci près qu’elle retourne un **DataRowView** tableau qui fait référence à toutes les lignes correspondantes dans le **DataView**. Si aucune correspondance n’est trouvée, le **DataRowView** tableau sera vide.  
  
 À utiliser le **trouver** ou **FindRows** méthodes, vous devez spécifier un tri en ordre soit en définissant **ApplyDefaultSort** à **true** ou à l’aide de la **Tri** propriété. Si aucun ordre de tri n'est spécifié, une exception est levée.  
  
 Le **trouver** et **FindRows** méthodes prennent un tableau de valeurs comme entrée dont la longueur correspond au nombre de colonnes dans l’ordre de tri. Si un tri doit s'effectuer sur une seule colonne, vous pouvez passer une seule valeur. Pour les ordres de tri incluant plusieurs colonnes, vous passez un tableau d'objets. Notez que pour un tri sur plusieurs colonnes, les valeurs du tableau d’objet doivent correspondre à l’ordre des colonnes spécifiées dans le **tri** propriété de la **DataView**.  
  
 Montre l’exemple de code suit le **trouver** méthode appelée sur un **DataView** avec un ordre de tri de colonne unique.  
  
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
  
 Si votre **tri** propriété spécifie plusieurs colonnes, vous devez passer un tableau d’objets avec les valeurs de recherche pour chaque colonne dans l’ordre spécifié par le **tri** propriété, comme dans l’exemple de code suivant.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
