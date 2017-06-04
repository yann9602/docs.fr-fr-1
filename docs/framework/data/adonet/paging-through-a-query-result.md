---
title: "Affichage des r&#233;sultats d&#39;une requ&#234;te sous forme de pages | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Affichage des r&#233;sultats d&#39;une requ&#234;te sous forme de pages
Ce mode d'affichage consiste à retourner les résultats d'une requête sous forme de sous\-ensembles, plus petits, de données, aussi appelés pages.  Cette façon de procéder est courante lorsqu'il s'agit de présenter à l'utilisateur un affichage des résultats par petits segments, plus faciles à gérer.  
  
 Le **DataAdapter** propose une fonctionnalité permettant de retourner uniquement une page de données, grâce aux surcharges de la méthode **Fill**.  Toutefois, cette solution n'est pas la mieux adaptée lorsque les résultats de la requête sont très volumineux car, si le **DataAdapter** remplit l'objet <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> cible uniquement avec les enregistrements demandés, les ressources sollicitées restent les mêmes que pour retourner l'intégralité de la requête.  Pour retourner une page de données provenant d'une source de donnée sans solliciter les ressources requises pour retourner l'intégralité de la requête, spécifiez des critères supplémentaires pour votre requête afin de limiter le nombre de lignes retournées à celles qui sont requises.  
  
 Pour utiliser la méthode **Fill** afin de retourner une page de données, spécifiez un paramètre **startRecord** indiquant le premier enregistrement de la page de données et un paramètre **maxRecords** indiquant le nombre d'enregistrements de la page de données.  
  
 L'exemple de code suivant montre comment utiliser la méthode **Fill** pour retourner la première page des résultats d'une requête, sachant que la page comptera cinq enregistrements.  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Dans l'exemple précédent, le **DataSet** ne reçoit que cinq enregistrements, mais la table **Orders** est retournée dans son intégralité.  Pour remplir le **DataSet** avec ces cinq mêmes enregistrements, mais en ne retournant que cinq enregistrements, utilisez les clauses TOP et WHERE dans votre instruction SQL, comme dans l'exemple de code suivant.  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 Notez que, lorsque vous choisissez ce mode d'affichage par pages des résultats d'une requête, vous devez conserver l'identificateur unique en fonction duquel les lignes sont organisées, afin de passer cet identificateur unique à la commande pour retourner la page d'enregistrements suivante, comme le montre l'exemple de code ci\-après.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Pour retourner la page d'enregistrements suivante à l'aide de la surcharge de la méthode **Fill** qui accepte les paramètres **startRecord** et **maxRecords**, incrémentez l'index de l'enregistrement en cours en fonction de la taille de la page \(exprimée en nombre d'enregistrements par page\) et remplissez la table.  N'oubliez pas que le serveur de base de données retourne l'intégralité des résultats de la requête, même si une seule page d'enregistrements est ajoutée au **DataSet**.  Dans l'exemple de code suivant, les lignes de la table sont vidées de leur contenu avant de recevoir la page de données suivante.  Vous avez la possibilité de conserver dans un cache local un certain nombre de lignes retournées afin de limiter les sollicitations du serveur de base de données.  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Pour retourner la page d'enregistrements suivante sans que le serveur de base de données ne retourne l'intégralité de la requête, spécifiez des critères restrictifs pour l'instruction SELECT.  Parce que l'exemple précédent conservait le dernier enregistrement retourné, vous pouvez l'utiliser dans la clause WHERE afin de spécifier le point de départ de la requête, comme le montre l'exemple de code suivant.  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## Voir aussi  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)