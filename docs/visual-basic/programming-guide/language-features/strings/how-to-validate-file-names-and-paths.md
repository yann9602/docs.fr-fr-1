---
title: "Comment : valider des noms de fichiers et des chemins d’accès en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Comment : valider des noms de fichiers et des chemins d’accès en Visual Basic
Cet exemple retourne un `Boolean` valeur qui indique si une chaîne représente un nom de fichier ou le chemin d’accès. La validation vérifie si le nom contient des caractères qui ne sont pas autorisées par le système de fichiers.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Cet exemple ne vérifie pas si le nom a placé de manière incorrecte des signes deux-points ou des répertoires sans nom, ou si la longueur du nom dépasse la longueur maximale définie par le système. Il également ne vérifie pas si l’application a l’autorisation d’accéder à la ressource du système de fichiers avec le nom spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
