---
title: "Réflexion (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ae042933575849e105d7b681634a61319c1d6ee
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-visual-basic"></a>Réflexion (Visual Basic)
La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent les types, les modules et assemblys.</xref:System.Type> Vous pouvez utiliser la réflexion pour dynamiquement créer une instance d’un type, le type de liaison à un objet existant, obtenir le type d’un objet existant et appeler ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [attributs](https://msdn.microsoft.com/library/5x6cd29c).  
  
 Voici un exemple simple de réflexion à l’aide de la méthode statique `GetType` , héritée par tous les types à partir de la `Object` classe - pour obtenir le type d’une variable de base :  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Le résultat est :  
  
 `System.Int32`  
  
 L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Le résultat est :  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Vue d’ensemble de la réflexion  
 La réflexion est utile dans les situations suivantes :  
  
-   Lorsque vous devez accéder aux attributs dans les métadonnées de votre programme. Pour plus d’informations, consultez [récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).  
  
-   Pour examiner et instancier des types dans un assembly.  
  
-   Pour la création de nouveaux types pendant l’exécution. Utiliser des classes dans <xref:System.Reflection.Emit>.</xref:System.Reflection.Emit>  
  
-   Pour effectuer une liaison tardive, l’accès aux méthodes sur les types créés au moment de l’exécution. Consultez la rubrique [à l’aide de Types et de chargement dynamique](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Réflexion](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [Affichage des informations de Type](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [Réflexion et Types génériques](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit></xref:System.Reflection.Emit>  
  
-   [Récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)   
 [Assemblys dans le Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)
