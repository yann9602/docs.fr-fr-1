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
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="6244e-102">Déploiement d’applications qui font référence à des contrôles Power Packs (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6244e-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="6244e-103">Si vous souhaitez déployer une application qui référence les contrôles Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), les contrôles doivent être installés sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="6244e-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="6244e-104">Installer les contrôles Power Packs comme condition préalable</span><span class="sxs-lookup"><span data-stu-id="6244e-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="6244e-105">Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application.</span><span class="sxs-lookup"><span data-stu-id="6244e-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="6244e-106">Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.</span><span class="sxs-lookup"><span data-stu-id="6244e-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="6244e-107">Lorsque [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] est installé sur votre ordinateur de développement, un Power Packs package du programme d’amorçage est ajouté à la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] répertoire du programme d’amorçage.</span><span class="sxs-lookup"><span data-stu-id="6244e-107">When [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="6244e-108">Ce package est alors disponible quand vous suivez les procédures d’ajout des composants prérequis pour le déploiement de [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="6244e-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="6244e-109">Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation.</span><span class="sxs-lookup"><span data-stu-id="6244e-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="6244e-110">Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6244e-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6244e-111">Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6244e-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="6244e-112">Pour les applications [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] , cela signifie que l’utilisateur a besoin d’autorisations d’administration pour installer l’application, quel que soit le niveau de sécurité spécifié par celle-ci.</span><span class="sxs-lookup"><span data-stu-id="6244e-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="6244e-113">Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.</span><span class="sxs-lookup"><span data-stu-id="6244e-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="6244e-114">Pendant l’installation, les utilisateurs seront invités à installer les contrôles Power Packs s’ils ne sont pas présents sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="6244e-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="6244e-115">Comme alternative à l’amorçage, vous pouvez prédéployer les contrôles Power Packs à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="6244e-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6244e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6244e-116">See also</span></span>  
 [<span data-ttu-id="6244e-117">Guide pratique pour installer des composants prérequis avec une application ClickOnce</span><span class="sxs-lookup"><span data-stu-id="6244e-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="6244e-118">Contrôles Visual Basic Power Packs</span><span class="sxs-lookup"><span data-stu-id="6244e-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
