---
title: "Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b625e0c58653f1ee9a2d263d7d2d29ad3b2e3c1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="a681d-102">Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a681d-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="a681d-103">Si vous souhaitez déployer une application qui référence le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant, le composant doit être installé sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="a681d-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="a681d-104">Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="a681d-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="a681d-105">Installation de PrintForm en tant que composant requis</span><span class="sxs-lookup"><span data-stu-id="a681d-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="a681d-106">Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application.</span><span class="sxs-lookup"><span data-stu-id="a681d-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="a681d-107">Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.</span><span class="sxs-lookup"><span data-stu-id="a681d-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="a681d-108">Lorsque le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant est installé sur votre ordinateur de développement, un package de programme d’amorçage de Microsoft Visual Basic Power Packs est ajouté à la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] répertoire du programme d’amorçage.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="a681d-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="a681d-109">Ce package est alors disponible lorsque vous suivez les procédures d’ajout de conditions préalables pour le [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou le déploiement de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="a681d-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="a681d-110">Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation.</span><span class="sxs-lookup"><span data-stu-id="a681d-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="a681d-111">Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a681d-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a681d-112">Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a681d-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="a681d-113">Pour [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, cela signifie que l’utilisateur a besoin d’autorisations administratives pour installer l’application, quel que soit le niveau de sécurité spécifié par l’application.</span><span class="sxs-lookup"><span data-stu-id="a681d-113">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="a681d-114">Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.</span><span class="sxs-lookup"><span data-stu-id="a681d-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="a681d-115">Pendant l’installation, les utilisateurs seront invités à installer le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant si elle n’est pas présent sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="a681d-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="a681d-116">Comme alternative à l’amorçage, vous pouvez pré-déployer le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="a681d-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a681d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a681d-117">See also</span></span>  
 <span data-ttu-id="a681d-118">[Comment : installer les composants requis avec une Application ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="a681d-118">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="a681d-119"> [PrintForm, composant](../../../visual-basic/developing-apps/printing/printform-component.md)</span><span class="sxs-lookup"><span data-stu-id="a681d-119"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)</span></span>
