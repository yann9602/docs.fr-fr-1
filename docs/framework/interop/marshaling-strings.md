---
title: "Marshaling Strings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "marshaling, samples"
  - "platform invoke, marshaling data"
  - "data marshaling, strings"
  - "data marshaling, samples"
  - "data marshaling, platform invoke"
  - "marshaling. strings"
  - "marshaling, platform invoke"
  - "sample applications [.NET Framework], marshaling strings"
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Marshaling Strings
L'appel de code non managé copie des paramètres de chaînes, en les convertissant du format .NET Framework \(Unicode\) au format non managé \(ANSI\), si nécessaire.  Comme les chaînes managées sont immuables, l'appel de code non managé ne les recopie pas à partir de la mémoire non managée vers la mémoire managée au retour de fonction.  
  
 Le tableau suivant répertorie les options de marshaling pour les chaînes, décrit leur usage et fournit un lien vers l'exemple correspondant du .NET Framework.  
  
|Chaîne|Description|Exemples|  
|------------|-----------------|--------------|  
|Par valeur|Passe des chaînes en tant que paramètres en entrée.|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|Comme résultat.|Retourne des chaînes à partir du code non managé.|[Chaînes](http://msdn.microsoft.com/fr-fr/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Par référence.|Passe des chaînes en tant que paramètres en entrée\/sortie à l'aide de <xref:System.Text.StringBuilder>.|[Buffers](http://msdn.microsoft.com/fr-fr/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|Dans une structure par valeur.|Passe des chaînes dans une structure qui est un paramètre en entrée.|[Structures](http://msdn.microsoft.com/fr-fr/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|Dans une structure par référence **\(char\*\)**.|Passe des chaînes dans une structure qui est un paramètre en entrée\/sortie.  La fonction non managée nécessite un pointeur vers une mémoire tampon de caractères et la taille de la mémoire tampon fait partie de la structure.|[Chaînes](http://msdn.microsoft.com/fr-fr/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Dans une structure par référence **\(char\[\]\)**.|Passe des chaînes dans une structure qui est un paramètre en entrée\/sortie.  La fonction non managée nécessite une mémoire tampon de caractères incorporée.|[OSInfo](http://msdn.microsoft.com/fr-fr/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Dans une classe par valeur **\(char\*\)**.|Passe des chaînes dans une classe \(une classe est un paramètre en entrée\/sortie\).  La fonction non managée nécessite un pointeur vers une mémoire tampon de caractères.|[OpenFileDlg](http://msdn.microsoft.com/fr-fr/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|Dans une classe par valeur **\(char\[\]\)**.|Passe des chaînes dans une classe \(une classe est un paramètre en entrée\/sortie\).  La fonction non managée nécessite une mémoire tampon de caractères incorporée.|[OSInfo](http://msdn.microsoft.com/fr-fr/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Comme tableau de chaînes par valeur.|Crée un tableau de chaînes passé par valeur.|[Tableaux](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Comme tableau de structures qui contient des chaînes par valeur.|Crée un tableau de structures qui contient des chaînes. Le tableau est passé par valeur.|[Tableaux](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## Voir aussi  
 [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/fr-fr/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Marshaling Classes, Structures, and Unions](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)   
 [Marshaling Arrays of Types](http://msdn.microsoft.com/fr-fr/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)   
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/fr-fr/a915c948-54e9-4d0f-a525-95a77fd8ed70)