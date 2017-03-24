---
title: "LINQ et répertoires de fichiers (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
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
ms.openlocfilehash: 5536ae95b42cdaddda2c4cae97a114681e94b0ab
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ et répertoires de fichiers (Visual Basic)
Plusieurs opérations de système de fichiers sont des requêtes et sont donc parfaitement à l’approche LINQ.  
  
 Notez que les requêtes de cette section sont non destructif. Ils ne sont pas utilisés pour modifier le contenu des fichiers d’origine. Conformément à la règle que les requêtes ne devraient pas entraîner des effets secondaires. En règle générale, tout code (y compris les requêtes qui effectuent créent / mettre à jour / suppression des opérateurs) qui modifie les données sources doit rester distinct du code qui interroge uniquement les données.  
  
 Cette section contient les rubriques suivantes :  
  
 [Comment : interroger des fichiers possédant un attribut spécifié ou un nom (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Montre comment rechercher des fichiers en examinant une ou plusieurs propriétés de son <xref:System.IO.FileInfo>objet.</xref:System.IO.FileInfo>  
  
 [Comment : regrouper des fichiers par Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Montre comment retourner des groupes de <xref:System.IO.FileInfo>objet selon leur extension de nom de fichier.</xref:System.IO.FileInfo>  
  
 [Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Montre comment retourner le nombre total d’octets dans tous les fichiers dans une arborescence de répertoires spécifiée.  
  
 [Comment : comparer le contenu de deux dossiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Montre comment retourner tous les fichiers qui sont présents dans deux dossiers spécifiés et également tous les fichiers qui sont présents dans un dossier, mais pas l’autre.  
  
 [Comment : interroger le plus grand nombre ou les fichiers dans une arborescence de répertoires (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Montre comment retourner le fichier plus grand ou plus petit, ou un nombre spécifié de fichiers, dans une arborescence de répertoires.  
  
 [Comment : interroger des fichiers dupliqués dans une arborescence de répertoires (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Montre comment regrouper tous les noms de fichier qui se produisent dans plusieurs emplacements dans une arborescence de répertoires spécifiée. Montre également comment effectuer des comparaisons plus complexes selon un comparateur personnalisé.  
  
 [Comment : interroger le contenu de fichiers dans un dossier (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Montre comment effectuer une itération dans les dossiers dans une arborescence, ouvrez chaque fichier et interroger le contenu du fichier.  
  
## <a name="comments"></a>Commentaires  
 Il est plus complexe impliquées dans la création d’une source de données qui représente le contenu du système de fichiers et gère correctement les exceptions correctement. Les exemples dans cette section créent une collection instantanée de <xref:System.IO.FileInfo>des objets qui représentent tous les fichiers d’un dossier racine spécifié et tous ses sous-dossiers.</xref:System.IO.FileInfo> L’état réel de chaque <xref:System.IO.FileInfo>peuvent changer dans le temps entre le début et la fin de l’exécution d’une requête.</xref:System.IO.FileInfo> Par exemple, vous pouvez créer une liste de <xref:System.IO.FileInfo>des objets à utiliser comme source de données.</xref:System.IO.FileInfo> Si vous essayez d’accéder à la `Length` propriété dans une requête, le <xref:System.IO.FileInfo>objet tente d’accéder au système de fichiers pour mettre à jour la valeur de `Length`.</xref:System.IO.FileInfo> Si le fichier n’existe plus, vous obtiendrez un <xref:System.IO.FileNotFoundException>dans votre requête, même si vous n’interrogiez pas le système de fichiers directement.</xref:System.IO.FileNotFoundException> Certaines requêtes de cette section utilisent une méthode distincte qui utilise ces exceptions particulières dans certains cas. Une autre option consiste à conserver votre source de données mis à jour dynamiquement en utilisant le <xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher>  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
