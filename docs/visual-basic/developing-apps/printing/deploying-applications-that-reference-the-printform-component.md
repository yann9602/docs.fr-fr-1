---
title: "Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="e772f-102">Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e772f-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="e772f-103">Si vous voulez déployer une application qui fait référence au composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> , le composant doit être installé sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="e772f-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="e772f-104">Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="e772f-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="e772f-105">Installation de PrintForm comme composant requis</span><span class="sxs-lookup"><span data-stu-id="e772f-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="e772f-106">Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application.</span><span class="sxs-lookup"><span data-stu-id="e772f-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="e772f-107">Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.</span><span class="sxs-lookup"><span data-stu-id="e772f-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="e772f-108">Quand le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est installé sur votre ordinateur de développement, un package de programme d’amorçage Microsoft Visual Basic Power Packs est ajouté au répertoire du programme d’amorçage [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e772f-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="e772f-109">Ce package est alors disponible quand vous suivez les procédures d’ajout des composants prérequis pour le déploiement de [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="e772f-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="e772f-110">Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation.</span><span class="sxs-lookup"><span data-stu-id="e772f-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="e772f-111">Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e772f-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e772f-112">Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e772f-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="e772f-113">Pour les applications [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] , cela signifie que l’utilisateur a besoin d’autorisations d’administration pour installer l’application, quel que soit le niveau de sécurité spécifié par celle-ci.</span><span class="sxs-lookup"><span data-stu-id="e772f-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="e772f-114">Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.</span><span class="sxs-lookup"><span data-stu-id="e772f-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="e772f-115">Lors de l’installation, les utilisateurs sont invités à installer le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> s’il n’est pas présent sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="e772f-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="e772f-116">À la place de l’amorçage, vous pouvez prédéployer le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> à l’aide d’un système électronique de distribution de logiciels, par exemple Microsoft Systems Management Server (SMS).</span><span class="sxs-lookup"><span data-stu-id="e772f-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e772f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e772f-117">See also</span></span>  
 [<span data-ttu-id="e772f-118">Guide pratique pour installer des composants prérequis avec une application ClickOnce</span><span class="sxs-lookup"><span data-stu-id="e772f-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="e772f-119">PrintForm, composant</span><span class="sxs-lookup"><span data-stu-id="e772f-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
