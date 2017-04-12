---
title: "Valeur de type &quot;&lt;NomType1&gt;« ne peut pas être converti en »&lt;NomType2&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c973d5e2aa03d423e1dea8053946172655f08490
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>Valeur de type '&lt;NomType1&gt;« ne peut pas être converti en »&lt;NomType2&gt;»
Valeur de type '\<NomType1 >' ne peut pas être convertie en '\<NomType2 > ». Incompatibilité de type peut être dû à la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<assemblyname > ». Essayez de remplacer la référence du fichier à '\<filepath >' projet '\<projectname1 >' avec une référence de projet à '\<projectname2 > ».  
  
 Dans une situation où un projet crée une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.  
  
 Le pseudo-code suivant illustre une situation qui peut générer cette erreur.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projet `P1` établit une référence de projet indirecte via le projet `P2` au projet `P3`, ainsi qu’une référence de fichier directe pour `P3`. La déclaration de `commonObject` utilise la référence de fichier pour `P3`, tandis que l’appel à `P2.getCommonClass` utilise la référence de projet `P3`.  
  
 Le problème dans ce cas est que la référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie de `P3` (en général, p3.dll), alors que les références de projet identifient le projet source (`P3`) par le nom du projet. Pour cette raison, le compilateur ne peut pas garantir que le type `P3.commonClass` proviennent du même code source, les deux références différentes.  
  
 Cette situation se produit généralement lorsque les références de projet et les références de fichiers sont mélangées. Dans l’illustration précédente, le problème se produirait pas si `P1` crée une référence de projet directe pour `P3` au lieu d’une référence de fichier.  
  
 **ID d’erreur :** BC30955  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Modifiez la référence de fichier pour une référence de projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions de type dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
