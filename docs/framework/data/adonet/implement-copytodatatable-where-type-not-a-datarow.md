---
title: "Proc&#233;dure&#160;: impl&#233;menter CopyToDataTable&lt;T&gt; o&#249; le type g&#233;n&#233;rique&#160;T n&#39;est pas un DataRow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: impl&#233;menter CopyToDataTable&lt;T&gt; o&#249; le type g&#233;n&#233;rique&#160;T n&#39;est pas un DataRow
L'objet <xref:System.Data.DataTable> est souvent utilisé pour la liaison de données.  La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> prend les résultats d'une requête et copie les données dans un objet <xref:System.Data.DataTable> qui peut ensuite être utilisé pour la liaison de données.  Toutefois, les méthodes <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> ne fonctionneront que sur une source <xref:System.Collections.Generic.IEnumerable%601> où le paramètre générique `T` est de type <xref:System.Data.DataRow>.  Bien qu'utile, cela ne permet pas de créer des tables à partir d'une séquence de types scalaires, de requêtes qui projettent des types anonymes ou de requêtes qui effectuent des jointures de tables.  
  
 Cette rubrique décrit comment implémenter deux classes d'extension `CopyToDataTable<T>` personnalisées qui acceptent un paramètre générique `T` d'un type autre que <xref:System.Data.DataRow>.  La logique pour créer un objet <xref:System.Data.DataTable> à partir d'une source <xref:System.Collections.Generic.IEnumerable%601> est contenue dans la classe `ObjectShredder<T>`, laquelle est ensuite encapsulée dans deux méthodes d'extension `CopyToDataTable<T>` surchargées.  La méthode `Shred` de la classe `ObjectShredder<T>` retourne les objets <xref:System.Data.DataTable> remplis et accepte trois paramètres d'entrée : une source <xref:System.Collections.Generic.IEnumerable%601>, un objet <xref:System.Data.DataTable> et une énumération <xref:System.Data.LoadOption>.  Le schéma initial de l'objet <xref:System.Data.DataTable> retourné est basé sur le schéma du type `T`.  Si une table existante est fournie comme paramètre d'entrée, le schéma doit être cohérent avec le schéma du type `T`.  Chaque propriété publique et champ public du type `T` est converti en objet <xref:System.Data.DataColumn> dans la table retournée.  Si la séquence source contient un type dérivé de `T`, le schéma de table retourné est étendu pour toute propriété publique ou tout champ public supplémentaire.  
  
 Pour obtenir des exemples d'utilisation des méthodes `CopyToDataTable<T>` personnalisées, consultez [Création d'un DataTable à partir d'une requête](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### Pour implémenter les méthodes CopyToDataTable\<T\> personnalisées dans votre application  
  
1.  Implémentez la classe `ObjectShredder<T>` pour créer un objet <xref:System.Data.DataTable> à partir d'une source <xref:System.Collections.Generic.IEnumerable%601> :  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  Implémentez les méthodes d'extension `CopyToDataTable<T>` personnalisées dans une classe :  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Ajoutez la classe `ObjectShredder<T>` et les méthodes d'extension `CopyToDataTable<T>` à votre application.  
  
    ```vb  
    Module Module1  
        Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
        End Sub  
    End Module  
  
    Public Module CustomLINQtoDataSetMethods  
    …  
    End Module  
  
    Public Class ObjectShredder(Of T)  
    …  
    End Class  
    ```  
  
4.  ```c#  
    class Program  
    {  
            static void Main(string[] args)  
            {  
               // Your application code using CopyToDataTable<T>.  
            }  
    }  
    public static class CustomLINQtoDataSetMethods  
    {  
    …  
    }  
    public class ObjectShredder<T>  
    {  
    …  
    }  
    ```  
  
## Voir aussi  
 [Création d'un DataTable à partir d'une requête](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)   
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)