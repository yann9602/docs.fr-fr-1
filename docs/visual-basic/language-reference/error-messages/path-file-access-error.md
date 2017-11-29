---
title: "Erreur d’accès de chemin d’accès de fichier"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>Erreur dans le chemin d’accès
Pendant une opération d’accès au fichier ou l’accès au disque, le système d’exploitation ne peut pas établir une connexion entre le chemin d’accès et le nom de fichier.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que la spécification de fichier est correctement formatée. Un nom de fichier peut contenir un qualifié complet (absolu) ou par rapport chemin d’accès. Un chemin d’accès qualifié complet commence par le nom du lecteur (si le chemin d’accès est sur un autre lecteur) et répertorie le chemin d’accès explicite à partir de la racine du fichier. N’importe quel chemin d’accès qui n’est pas qualifié complet est relatif au lecteur actif et au répertoire.  
  
2.  Assurez-vous que vous n’avez pas tenté d’enregistrer un fichier qui remplace un fichier en lecture seule existant. Si c’est le cas, modifiez l’attribut en lecture seule du fichier cible ou enregistrez le fichier avec un autre nom de fichier.  
  
3.  Assurez-vous que vous n’avez pas tenté d’ouvrir un fichier en lecture seule dans séquentiel `Output` ou `Append` mode. Si c’est le cas, ouvrez le fichier dans `Input` mode ou modifiez l’attribut en lecture seule du fichier.  
  
4.  Assurez-vous que vous n’avez pas tenté de modifier un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projet au sein d’une base de données ou un document.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)
