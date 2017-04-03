---
title: "Réflexion (C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab40ab2258703670576084eccf7fd7e1b113d08d
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-c"></a>Réflexion (C#)
La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent des assemblys, des modules et des types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [Attributs](https://msdn.microsoft.com/library/5x6cd29c).  
  
 Voici un exemple simple de réflexion utilisant la méthode statique `GetType`, héritée par tous les types à partir de la classe de base `Object`, pour obtenir le type d’une variable :  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 La sortie est la suivante :  
  
 `System.Int32`  
  
 L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 La sortie est la suivante :  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion. Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*. Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>. Pour identifier une méthode `protected internal`, utilisez la propriété <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Vue d’ensemble de la réflexion  
 La réflexion est utile dans les situations suivantes :  
  
-   Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme. Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).  
  
-   Pour examiner et instancier des types dans un assembly.  
  
-   Pour créer de nouveaux types au moment de l’exécution. Utilisez des classes dans <xref:System.Reflection.Emit>.  
  
-   Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution. Consultez la rubrique [Chargement et utilisation dynamiques des types](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Réflexion](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [Affichage des informations de type](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [Réflexion et types génériques](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Assemblys dans le Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)
