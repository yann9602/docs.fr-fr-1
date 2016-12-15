---
title: "Unable to emit assembly: &lt;error message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30145"
  - "bc30145"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30145"
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unable to emit assembly: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle Assembly Linker \(Al.exe, également appelé Alink\) pour générer un assembly avec un manifeste, avec l'éditeur de liens qui signale une erreur dans la phase d'émission de création de l'assembly.  
  
 **ID d'erreur :** BC30145  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d'erreur cité et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pour obtenir davantage d'explications et de conseils.  
  
2.  Essayez de signer manuellement l'assembly, à l'aide d'[Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) ou de l'outil [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
3.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
### Pour signer manuellement l'assembly  
  
1.  Utilisez l'outil [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) pour créer un fichier de paire de clés publiques\/privées.  
  
     Ce fichier porte l'extension .snk.  
  
2.  Supprimez la référence COM qui génère l'erreur de votre projet.  
  
3.  Dans le menu **Démarrer** de Windows, pointez sur **Programmes**, sur **Microsoft Visual Studio 2008**, sur **Visual Studio Tools**, puis cliquez sur **Invite de commandes de Visual Studio 2008**.  
  
4.  Accédez au répertoire dans lequel vous voulez placer le wrapper d'assembly.  
  
5.  Tapez le code suivant.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Voici un exemple du code que vous pouvez entrer.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Utilisez des guillemets doubles \("\) si un chemin ou un fichier contient des espaces.  
  
6.  Dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ajoutez une référence à un assembly .NET dans le fichier que vous venez de créer.  
  
## Voir aussi  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [Comment : créer une paire de clés publique\/privée](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [Nous contacter](/visual-studio/ide/talk-to-us)