---
title: "Proc&#233;dure&#160;: appeler des fonctions d&#233;finies par mod&#232;le comme des m&#233;thodes d&#39;objet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: appeler des fonctions d&#233;finies par mod&#232;le comme des m&#233;thodes d&#39;objet
Cette rubrique décrit comment appeler une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext> ou comme une méthode statique sur une classe personnalisée.  Une *fonction définie par modèle* est une fonction qui est définie dans le modèle conceptuel.  Les procédures décrites dans cette rubrique montrent comment appeler directement ces fonctions au lieu de les appeler à partir de requêtes LINQ to Entities.  Pour plus d'informations sur l'appel de fonctions définies par modèle dans des requêtes LINQ to Entities, consultez [Procédure : appeler des fonctions définies par modèle dans des requêtes](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Si vous appelez une fonction définie par modèle comme une méthode <xref:System.Data.Objects.ObjectContext> ou comme une méthode statique sur une classe personnalisée, vous devez mapper en premier la méthode à la fonction définie par modèle avec un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  Toutefois, lorsque vous définissez une méthode sur la classe <xref:System.Data.Objects.ObjectContext>, vous devez utiliser la propriété <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> pour exposer le fournisseur LINQ, alors que lorsque vous définissez une méthode statique sur une classe personnalisée, vous devez utiliser la propriété <xref:System.Linq.IQueryable.Provider%2A> pour exposer le fournisseur LINQ.  Pour plus d'informations, consultez les exemples qui suivent les procédures ci\-dessous.  
  
 Les procédures suivantes fournissent une présentation de haut niveau pour l'appel d'une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext> et comme une méthode statique sur une classe personnalisée.  Les exemples qui suivent fournissent plus de détail sur les étapes des procédures.  Les procédures supposent que vous avez défini une fonction dans le modèle conceptuel.  Pour plus d'informations, consultez [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/fr-fr/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### Pour appeler une fonction définie par modèle comme une méthode sur un objet ObjectContext  
  
1.  Ajoutez un fichier source pour étendre la classe partielle dérivée de la classe <xref:System.Data.Objects.ObjectContext>, générée automatiquement par les outils Entity Framework.  La définition du stub de CLR dans un fichier source distinct empêche la perte des modifications lorsque le fichier est régénéré.  
  
2.  Ajoutez une méthode CLR \(Common Language Runtime\) à votre classe <xref:System.Data.Objects.ObjectContext> qui effectue les opérations suivantes :  
  
    -   Elle est mappée à la fonction définie dans le modèle conceptuel.  Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent au nom de l'espace de noms du modèle conceptuel et au nom de la fonction dans le modèle conceptuel, respectivement.  La résolution des noms de fonctions pour LINQ respecte la casse.  
  
    -   Elle retourne les résultats de la méthode <xref:System.Linq.IQueryProvider.Execute%2A> retournée par la propriété <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>.  
  
3.  Appelez la méthode en tant que membre sur une instance de la classe <xref:System.Data.Objects.ObjectContext>.  
  
### Pour appeler une fonction définie par modèle comme une méthode statique sur une classe personnalisée  
  
1.  Ajoutez une classe à votre application avec une méthode statique qui effectue les opérations suivantes :  
  
    -   Elle est mappée à la fonction définie dans le modèle conceptuel.  Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent au nom de l'espace de noms du modèle conceptuel et au nom de la fonction dans le modèle conceptuel, respectivement.  
  
    -   Elle accepte un argument <xref:System.Linq.IQueryable>.  
  
    -   Elle retourne les résultats de la méthode <xref:System.Linq.IQueryProvider.Execute%2A> retournée par la propriété <xref:System.Linq.IQueryable.Provider%2A>.  
  
2.  Appelez la méthode comme méthode statique sur la classe personnalisée.  
  
## Exemple  
 **Appel d'une fonction définie par modèle comme une méthode sur un objet ObjectContext**  
  
 L'exemple suivant montre comment appeler une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext>.  L'exemple utilise le [modèle de vente AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Considérez la fonction de modèle conceptuel ci\-dessous qui retourne le revenu généré par un produit donné.  \(Pour plus d'informations sur l'ajout de la fonction dans le modèle conceptuel, consultez [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/fr-fr/0dad7b8b-58f6-4271-b238-f34810d68e5f).\)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#4)]
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#4)]
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  
  
## Exemple  
 Le code suivant ajoute une méthode à la classe `AdventureWorksEntities` qui est mappée à la fonction de modèle conceptuel ci\-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## Exemple  
 Le code suivant appelle la méthode ci\-dessus pour afficher le revenu généré par un produit donné :  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## Exemple  
 L'exemple suivant montre comment appeler une fonction définie par modèle qui retourne une collection \(en tant qu'objet <xref:System.Linq.IQueryable%601>\).  Considérez la fonction de modèle conceptuel ci\-dessous qui retourne tous les détails `SalesOrderDetails` pour un ID de produit donné.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## Exemple  
 Le code suivant ajoute une méthode à la classe `AdventureWorksEntities` qui est mappée à la fonction de modèle conceptuel ci\-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## Exemple  
 Le code suivant appelle la méthode.  Notez que la requête <xref:System.Linq.IQueryable%601> retournée est encore affinée pour retourner les totaux de ligne pour chaque `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## Exemple  
 **Appel d'une fonction définie par modèle comme une méthode statique sur une classe personnalisée**  
  
 L'exemple suivant montre comment appeler une fonction définie par modèle comme une méthode statique sur une classe personnalisée.  L'exemple utilise le [modèle de vente AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Lorsque vous appelez une fonction définie par modèle comme une méthode statique sur une classe personnalisée, la fonction définie par modèle doit accepter une collection et retourner une agrégation de valeurs dans la collection.  
  
 Considérez la fonction de modèle conceptuel ci\-dessous, qui retourne le revenu produit pour une collection SalesOrderDetail.  \(Pour plus d'informations sur l'ajout de la fonction dans le modèle conceptuel, consultez [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/fr-fr/0dad7b8b-58f6-4271-b238-f34810d68e5f).\)  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#1)]
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#1)]
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]  
  
## Exemple  
 Le code suivant ajoute une classe à votre application qui contient une méthode statique mappée à la fonction de modèle conceptuel ci\-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## Exemple  
 Le code suivant appelle la méthode ci\-dessus pour afficher le revenu produit pour une collection SalesOrderDetail :  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## Voir aussi  
 [.edmx File Overview](http://msdn.microsoft.com/fr-fr/f4c8e7ce-1db6-417e-9759-15f8b55155d4)   
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)   
 [Appel de fonctions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)