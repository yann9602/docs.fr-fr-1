---
title: "Réflexion (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2ae87eae971129059a7e84b36971c13a5fe71b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-visual-basic"></a>Réflexion (Visual Basic)
La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent des assemblys, des modules et des types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [Attributs](../../../../docs/standard/attributes/index.md).  
  
 Voici un exemple simple de réflexion utilisant la méthode statique `GetType`, héritée par tous les types à partir de la classe de base `Object`, pour obtenir le type d’une variable :  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 La sortie est la suivante :  
  
 `System.Int32`  
  
 L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 La sortie est la suivante :  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Vue d’ensemble de la réflexion  
 La réflexion est utile dans les situations suivantes :  
  
-   Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme. Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
-   Pour examiner et instancier des types dans un assembly.  
  
-   Pour créer de nouveaux types au moment de l’exécution. Utilisez des classes dans <xref:System.Reflection.Emit>.  
  
-   Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution. Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Réflexion](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [Affichage des informations de type](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [Réflexion et types génériques](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)  
 [Assemblys dans le Common Language Runtime](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
