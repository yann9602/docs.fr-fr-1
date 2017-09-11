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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ad1aba4f2e725abbe560f0c71fbb543e15741200
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="df980-102">Déploiement d’applications faisant référence aux contrôles Power Packs (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="df980-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="df980-103">Si vous souhaitez déployer une application qui référence les contrôles Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), les contrôles doivent être installés sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="df980-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="df980-104">Installer les contrôles Power Packs en tant que composant requis</span><span class="sxs-lookup"><span data-stu-id="df980-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="df980-105">Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application.</span><span class="sxs-lookup"><span data-stu-id="df980-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="df980-106">Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.</span><span class="sxs-lookup"><span data-stu-id="df980-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="df980-107">Lors de la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] est installé sur votre ordinateur de développement, un Power Packs package de programme d’amorçage est ajouté à la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] répertoire du programme d’amorçage.</span><span class="sxs-lookup"><span data-stu-id="df980-107">When [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="df980-108">Ce package est alors disponible lorsque vous suivez les procédures d’ajout de conditions préalables pour le [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou le déploiement de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="df980-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="df980-109">Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation.</span><span class="sxs-lookup"><span data-stu-id="df980-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="df980-110">Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="df980-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df980-111">Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="df980-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="df980-112">Pour [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, cela signifie que l’utilisateur a besoin d’autorisations administratives pour installer l’application, quel que soit le niveau de sécurité spécifié par l’application.</span><span class="sxs-lookup"><span data-stu-id="df980-112">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="df980-113">Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.</span><span class="sxs-lookup"><span data-stu-id="df980-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="df980-114">Pendant l’installation, les utilisateurs seront invités à installer les contrôles Power Packs si elles ne sont pas présents sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="df980-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="df980-115">Comme alternative à l’amorçage, vous pouvez pré-déployer les contrôles Power Packs à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="df980-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df980-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df980-116">See also</span></span>  
 <span data-ttu-id="df980-117">[Comment : installer les composants requis avec une Application ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="df980-117">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="df980-118"> [Contrôles Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span><span class="sxs-lookup"><span data-stu-id="df980-118"> [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span></span>
