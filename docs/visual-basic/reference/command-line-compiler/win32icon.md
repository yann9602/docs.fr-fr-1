---
title: "/win32icon | Microsoft Docs"
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
  - "win32icon compiler option [Visual Basic]"
  - "-win32icon compiler option [Visual Basic]"
  - "/win32icon compiler option [Visual Basic]"
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# /win32icon
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Insère un fichier .ico dans le fichier de sortie.  Ce fichier .ico représente le fichier de sortie dans **Explorateur de fichiers**.  
  
## Syntaxe  
  
```  
/win32icon:filename  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`filename`|Fichier .ico à ajouter au fichier de sortie.  Mettez le nom de fichier entre guillemets \(" "\) s'il contient un espace.|  
  
## Notes  
 Vous pouvez créer un fichier  .ico avec le compilateur de ressources \(RC\) Microsoft Windows.  Le compilateur de ressources est appelé lors de la compilation d'un programme Visual C\+\+ ; un fichier  .ico est alors créé à partir du fichier  .rc.  Les options `/win32icon` et `/win32resource` s'excluent mutuellement.  
  
 Consultez [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un fichier de ressource [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] ou [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) pour joindre un fichier de ressource [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Consultez [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) pour importer un fichier  .res.  
  
||  
|-|  
|Pour définir \/win32icon dans l'IDE de Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Application**.<br />3.  Modifiez la valeur dans la zone **Icône**.|  
  
## Exemple  
 Le code suivant compile `In.vb` et attache un fichier  .ico `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)