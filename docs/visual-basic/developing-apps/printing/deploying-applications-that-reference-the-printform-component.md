---
title: "Deploying Applications That Reference the PrintForm Component (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "PrintForm component [Visual Basic], deploying"
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying Applications That Reference the PrintForm Component (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Si vous voulez déployer une application qui fait référence au composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>, le composant doit être installé sur l’ordinateur de destination.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## Installation de PrintForm comme composant requis  
 Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application. Le processus d’installation des composants prérequis est connu sous le nom d’*amorçage*.  
  
 Quand le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est installé sur votre ordinateur de développement, un package de programme d’amorçage Microsoft Visual Basic Power Packs est ajouté au répertoire du programme d’amorçage [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. Ce package est alors disponible quand vous suivez les procédures d’ajout des composants prérequis pour le déploiement de [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou de Windows Installer.  
  
 Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation. Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.  
  
> [!NOTE]
>  Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur. Pour les applications [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)], cela signifie que l’utilisateur a besoin d’autorisations d’administration pour installer l’application, quel que soit le niveau de sécurité spécifié par celle\-ci. Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.  
  
 Lors de l’installation, les utilisateurs sont invités à installer le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> s’il n’est pas présent sur l’ordinateur de destination.  
  
 À la place de l’amorçage, vous pouvez prédéployer le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> à l’aide d’un système électronique de distribution de logiciels, par exemple Microsoft Systems Management Server \(SMS\).  
  
## Voir aussi  
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Not in Build : Choix d’une stratégie de déploiement](http://msdn.microsoft.com/fr-fr/ecd632d8-063c-4028-b785-81bba045107b)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)