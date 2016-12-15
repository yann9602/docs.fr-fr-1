---
title: "Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt; | Microsoft Docs"
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
  - "vbc31019"
  - "bc31019"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31019"
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un problème s'est produit pendant la création du fichier.  
  
 Vous ne pouvez pas ouvrir un fichier de sortie pour écriture. Le fichier \(ou le dossier qui le contient\) est peut être ouvert pour un usage exclusif par un autre processus, ou a son attribut de lecture seule défini.  
  
 Les situations courantes dans lesquelles un fichier est ouvert de manière exclusive sont les suivantes :  
  
-   L'application est déjà en cours d'exécution et utilise ses fichiers. Pour résoudre ce problème, vérifiez que l'application n'est pas en cours d'exécution.  
  
-   Une autre application a ouvert le fichier. Pour résoudre ce problème, vérifiez qu'aucune autre application n'accède aux fichiers. Il n'est pas toujours évident de savoir quelle application accède à vos fichiers ; le cas échéant, le plus facile est de redémarrer l'ordinateur pour arrêter l'application.  
  
 Si au moins un des fichiers de sortie du projet est marqué en lecture seule, cette exception est levée.  
  
 **ID d'erreur :** BC31019  
  
### Pour corriger cette erreur  
  
1.  Recompilez le programme pour voir si l'erreur se produit à nouveau.  
  
2.  Le cas échéant, enregistrez votre travail et redémarrez [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].  
  
3.  Si l'erreur continue, redémarrez l'ordinateur.  
  
4.  Si l'erreur se produit à nouveau, réinstallez [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
5.  Si l'erreur persiste après la réinstallation, avertissez les services de support technique Microsoft.  
  
### Pour vérifier les attributs de fichier dans l'Explorateur de fichiers  
  
1.  Ouvrez le dossier qui vous intéresse.  
  
2.  Cliquez sur l'icône **Affichages**, puis choisissez **Détails**.  
  
3.  Cliquez avec le bouton droit sur l'en\-tête de colonne, puis choisissez **Attributs** dans la liste déroulante.  
  
### Pour modifier les attributs d'un fichier ou d'un dossier  
  
1.  Dans l'**Explorateur de fichiers**, cliquez avec le bouton droit sur le fichier ou le dossier, puis choisissez **Propriétés**.  
  
2.  Dans la section **Attributs** de l'onglet **Général**, décochez la case **Lecture seule**.  
  
3.  Appuyez sur **OK**.  
  
## Voir aussi  
 [Nous contacter](/visual-studio/ide/talk-to-us)