---
title: "Déploiement d’applications faisant référence aux contrôles Power Packs (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4d342e655dcfe18ed3b5fc1d2710571ed8e3369e
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Déploiement d’applications faisant référence aux contrôles Power Packs (Visual Studio)
Si vous souhaitez déployer une application qui référence les contrôles Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), les contrôles doivent être installés sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Installer les contrôles Power Packs en tant que composant requis  
 Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application. Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.  
  
 Lors de la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] est installé sur votre ordinateur de développement, un Power Packs package de programme d’amorçage est ajouté à la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] répertoire du programme d’amorçage. Ce package est alors disponible lorsque vous suivez les procédures d’ajout de conditions préalables pour le [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou le déploiement de Windows Installer.  
  
 Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation. Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.  
  
> [!NOTE]
>  Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur. Pour [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, cela signifie que l’utilisateur a besoin d’autorisations administratives pour installer l’application, quel que soit le niveau de sécurité spécifié par l’application. Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.  
  
 Pendant l’installation, les utilisateurs seront invités à installer les contrôles Power Packs si elles ne sont pas présents sur l’ordinateur de destination.  
  
 Comme alternative à l’amorçage, vous pouvez pré-déployer les contrôles Power Packs à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : installer les composants requis avec une Application ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [Contrôles Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
