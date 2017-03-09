---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30955"
  - "bc30955"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30955"
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La valeur de type '\<NomType1\>' ne peut pas être convertie en '\<NomType2\>'.L'incompatibilité de type peut résulter de la combinaison d'une référence de fichier et d'une référence de projet pour l'assembly '\<NomAssembly\>'.Essayez de remplacer la référence de fichier pour '\<CheminFichier\>' dans le projet '\<NomProjet1\>' par une référence de projet pour '\<NomProjet2\>'.'  
  
 Lorsqu'un projet crée une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu'un type soit converti en un autre.  
  
 Le pseudo\-code suivant illustre une situation qui peut générer cette erreur.  
  
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
  
 Le projet `P1` crée une référence de projet indirecte par l'intermédiaire du projet `P2` pour le projet `P3`, et une référence de fichier directe pour `P3`.  La déclaration de `commonObject` utilise la référence de fichier pour `P3`, alors que l'appel à `P2.getCommonClass` utilise la référence de projet pour `P3`.  
  
 Le problème dans ce cas est que la référence de fichier spécifie un chemin d'accès et un nom pour le fichier de sortie de `P3` \(en général, p3.dll\), alors que les références de projet identifient le projet source \(`P3`\) par le nom du projet.  De ce fait, le compilateur ne peut pas garantir que le type `P3.commonClass` provienne du même code source pour les deux références différentes.  
  
 Cette situation se produit généralement lorsque les références de projet et les références de fichier sont associées.  Dans l'illustration précédente, le problème ne se produirait pas si `P1` crée une référence de projet directe pour `P3` au lieu d'une référence de fichier.  
  
 **ID d'erreur :** BC30955  
  
### Pour corriger cette erreur  
  
-   Remplacez la référence de fichier par une référence de projet.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)