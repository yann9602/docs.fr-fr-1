---
title: "Comment&#160;: analyser des chemins d&#39;acc&#232;s dans Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "noms de fichier, analyse (Visual Basic)"
  - "analyse des chemins de fichier (Visual Basic)"
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Comment&#160;: analyser des chemins d&#39;acc&#232;s dans Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L’objet <xref:Microsoft.VisualBasic.FileIO.FileSystem> fournit plusieurs méthodes qui facilitent l’analyse des chemins de fichier.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> combine deux chemins et affiche un chemin combiné au format correct.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> retourne le chemin absolu du parent du chemin fourni.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> retourne un objet <xref:System.IO.FileInfo> qui peut être interrogé pour déterminer les propriétés du fichier, telles que son nom et son chemin.  
  
 Ne vous basez pas sur l’extension de nom de fichier pour déterminer le contenu d’un fichier. Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.  
  
### Pour déterminer le nom et le chemin d’un fichier  
  
-   Utilisez les propriétés <xref:System.IO.FileInfo.DirectoryName%2A> et <xref:System.IO.FileInfo.Name%2A> de l’objet <xref:System.IO.FileInfo> pour déterminer le nom et le chemin d’un fichier. Cet exemple détermine le nom et le chemin d’un fichier, puis les affiche.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### Pour combiner le nom et le répertoire d’un fichier en un chemin complet  
  
-   Utilisez la méthode `CombinePath`, en spécifiant le répertoire et le nom du fichier. Cet exemple combine les chaînes `folderPath` et `fileName` créées dans l’exemple précédent, puis affiche le résultat.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>   
 <xref:System.IO.FileInfo>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)