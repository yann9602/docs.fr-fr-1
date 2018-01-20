---
title: "Comment : appeler des fonctions définies par modèle dans les requêtes"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec20542ad452bcefbe2b6d286e68ad8bbfb5adb9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Comment : appeler des fonctions définies par modèle dans les requêtes
Cette rubrique explique comment appeler des fonctions définies dans le modèle conceptuel à partir de requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
 La procédure suivante fournit un plan de haut niveau pour appeler une fonction définie par modèle à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. L'exemple qui suit fournit plus de détails sur les étapes de la procédure. La procédure suppose que vous avez défini une fonction dans le modèle conceptuel. Pour plus d’informations, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Pour appeler une fonction définie dans le modèle conceptuel  
  
1.  Ajoutez une méthode CLR (Common Language Runtime) à votre application qui se mappe à la fonction définie dans le modèle conceptuel. Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent respectivement au nom de l'espace de noms du modèle conceptuel et au nom de la fonction du modèle conceptuel. La résolution des noms de fonctions pour LINQ respecte la casse.  
  
2.  Appelez la fonction dans une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment appeler une fonction définie dans le modèle conceptuel à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. L'exemple utilise le modèle School. Pour plus d’informations sur le modèle School, consultez [création de la base de données School](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) et [générer le fichier de .edmx scolaire](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 La fonction de modèle conceptuel suivante retourne le nombre d'années écoulées depuis l'embauche d'un formateur. Pour plus d’informations sur l’ajout de la fonction à un modèle conceptuel, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Exemple  
 Ensuite, ajoutez la méthode suivante à votre application et utilisez un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pour la mapper à la fonction de modèle conceptuel :  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez à présent appeler la fonction de modèle conceptuel à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Le code suivant appelle la méthode pour afficher tous les formateurs embauchés il y a plus de dix ans :  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [vue d’ensemble du fichier .edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Appel de fonctions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Guide pratique pour appeler des fonctions définies par modèle comme méthodes d’objet](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
