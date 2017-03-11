---
title: "Deploying Applications That Reference Power Packs Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Power Packs, deploying"
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Deploying Applications That Reference Power Packs Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Si vous voulez déployer une application qui référence les contrôles Power Packs  \(<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>\), vous devez préalablement installer ceux\-ci sur l'ordinateur de destination.  
  
## Installation des contrôles Power Packs en tant que condition préalable  
 Pour déployer avec succès une application, vous devez également déployer tous les composants qui sont référencés par l'application.  Le processus d'installation des composants requis est connu sous le nom d'*amorçage*.  
  
 Lorsque le composant [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] est installé sur votre ordinateur de développement, un package du programme d'amorçage de Power Packs est ajouté au répertoire du programme d'amorçage [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Ce package est alors disponible lorsque vous suivez les procédures pour l'ajout de conditions préalables soit pour [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)], soit pour le déploiement de Windows Installer.  
  
 Par défaut, les composants amorcés sont déployés à partir du même emplacement que le programme d'installation.  Vous pouvez également choisir de déployer les composants à partir d'une URL ou d'un emplacement de partage de fichiers à partir duquel les utilisateurs peuvent les télécharger selon les besoins.  
  
> [!NOTE]
>  Pour installer des composants amorcés, l'utilisateur peut avoir besoin d'autorisations administratives ou d'autorisations utilisateur similaires sur l'ordinateur.  Pour les applications [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)], cela signifie que l'utilisateur a besoin d'autorisations administratives pour procéder à l'installation, quel que soit le niveau de sécurité spécifié par l'application.  Après avoir installé l'application, l'utilisateur peut l'exécuter sans autorisation administrative.  
  
 Pendant l'installation, les utilisateurs seront invités à installer les contrôles Power Packs si ceux\-ci ne sont pas présents sur l'ordinateur de destination.  
  
 Comme alternative à l'amorçage, vous pouvez pré\-déployer les contrôles Power Packs à l'aide d'un système de distribution électronique de logiciels, tel que Microsoft Systems Management Server.  
  
## Voir aussi  
 [How to: Install Prerequisites in Windows Installer Deployment](http://msdn.microsoft.com/fr-fr/653fc868-2486-429c-b75e-2f9d0c7f6619)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Not in Build: Choosing a Deployment Strategy](http://msdn.microsoft.com/fr-fr/ecd632d8-063c-4028-b785-81bba045107b)   
 [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)