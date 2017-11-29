---
title: "Déploiement d’applications qui font référence à des contrôles Power Packs (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Déploiement d’applications qui font référence à des contrôles Power Packs (Visual Studio)
Si vous souhaitez déployer une application qui référence les contrôles Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), les contrôles doivent être installés sur l’ordinateur de destination.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Installer les contrôles Power Packs comme condition préalable  
 Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application. Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.  
  
 Lorsque [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] est installé sur votre ordinateur de développement, un Power Packs package du programme d’amorçage est ajouté à la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] répertoire du programme d’amorçage. Ce package est alors disponible quand vous suivez les procédures d’ajout des composants prérequis pour le déploiement de [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou de Windows Installer.  
  
 Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation. Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.  
  
> [!NOTE]
>  Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur. Pour les applications [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] , cela signifie que l’utilisateur a besoin d’autorisations d’administration pour installer l’application, quel que soit le niveau de sécurité spécifié par celle-ci. Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.  
  
 Pendant l’installation, les utilisateurs seront invités à installer les contrôles Power Packs s’ils ne sont pas présents sur l’ordinateur de destination.  
  
 Comme alternative à l’amorçage, vous pouvez prédéployer les contrôles Power Packs à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour installer des composants prérequis avec une application ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Contrôles Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
