---
title: "Erreur d’accès chemin-fichier | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: ac730bac76540331206daebe600445ca54cc15a9
ms.lasthandoff: 03/13/2017

---
# <a name="pathfile-access-error"></a>Erreur dans le chemin d’accès
Pendant une opération d’accès au fichier ou l’accès au disque, le système d’exploitation ne peut pas établir une connexion entre le chemin d’accès et le nom de fichier.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que la spécification de fichier est correctement formatée. Un nom de fichier peut contenir un complet (absolu) ou par rapport chemin d’accès. Un chemin d’accès qualifié complet commence par le nom du lecteur (si le chemin d’accès se trouve sur un autre lecteur) et répertorie le chemin d’accès explicite à partir de la racine dans le fichier. N’importe quel chemin d’accès qui n’est pas complet est relatif au lecteur en cours et active.  
  
2.  Assurez-vous que vous n’avez tenté pas enregistrer un fichier qui remplace un fichier existant en lecture seule. Si c’est le cas, modifiez l’attribut en lecture seule du fichier cible ou enregistrez le fichier avec un nom de fichier différent.  
  
3.  Assurez-vous que vous n’avez pas tenté d’ouvrir un fichier en lecture seule dans séquentiel`Output`ou `Append` mode. Si c’est le cas, ouvrez le fichier dans `Input` mode ou modifiez l’attribut en lecture seule du fichier.  
  
4.  Assurez-vous que vous n’avez pas tenté de modifier un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet au sein d’une base de données ou un document.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)
