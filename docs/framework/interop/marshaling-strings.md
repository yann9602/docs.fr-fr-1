---
title: "Marshaling de chaînes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8d8455d4f1b4dbb463176c06d680b2bd0b1ff9d9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-strings"></a>Marshaling de chaînes
L’appel de code non managé copie les paramètres de chaîne, en les convertissant si nécessaire du format .NET Framework (Unicode) au format non managé (ANSI). Étant donné que les chaînes managées sont immuables, l’appel de code non managé ne les recopie pas de la mémoire non managée vers la mémoire managée au retour de la fonction.  
  
 Le tableau suivant répertorie les options de marshaling pour les chaînes. Il décrit leur utilisation et fournit un lien vers l’exemple .NET Framework correspondant.  
  
|Chaîne|Description|Exemple|  
|------------|-----------------|------------|  
|Par valeur.|Passe les structures en tant que paramètres entrants.|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|Comme résultat.|Retourne les chaînes à partir du code non managé.|[Chaînes](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Par référence.|Passe des chaînes en tant que paramètres entrants/sortants avec <xref:System.Text.StringBuilder>.|[Mémoires tampons](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|Dans une structure par valeur.|Passe des chaînes dans une structure qui est un paramètre entrant.|[Structs](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|Dans une structure par référence **(char\*)**.|Passe des chaînes dans une structure qui est un paramètre entrant/sortant. La fonction non managée attend un pointeur vers une mémoire tampon de caractères ; la taille de la mémoire tampon est un membre de la structure.|[Chaînes](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Dans une structure par référence **(char[])**.|Passe des chaînes dans une structure qui est un paramètre entrant/sortant. La fonction non managée attend une mémoire tampon de caractères incorporée.|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Dans une classe par valeur **(char\*)**.|Passe des chaînes dans une classe (une classe est un paramètre entrant/sortant). La fonction non managée attend un pointeur vers une mémoire tampon de caractères.|[OpenFileDlg](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|Dans une classe par valeur **(char[])**.|Passe des chaînes dans une classe (une classe est un paramètre entrant/sortant). La fonction non managée attend une mémoire tampon de caractères incorporée.|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Comme tableau de chaînes par valeur.|Crée un tableau de chaînes qui est passé par valeur.|[Tableaux](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Comme un tableau de structures qui contiennent des chaînes par valeur.|Crée un tableau de structures qui contiennent des chaînes ; le tableau est passé par valeur.|[Tableaux](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Marshaling de donnée avec un appel de code non managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Types de données d’appel de code non managé](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Marshaling de classes, de structures, et d’unions](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)   
 [Marshaling des tableaux de types](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)   
 [Exemples divers de marshaling](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)

