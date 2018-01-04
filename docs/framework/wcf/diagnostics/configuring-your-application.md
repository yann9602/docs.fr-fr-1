---
title: Configuration de votre application
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fd6dba860906fb87d67e19148f13b70dc64136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-your-application"></a><span data-ttu-id="f9df9-102">Configuration de votre application</span><span class="sxs-lookup"><span data-stu-id="f9df9-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f9df9-103"> utilise le système de configuration .NET et vous permet de configurer des services à la fois au niveau de l'ordinateur et au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="f9df9-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="f9df9-104">Les paramètres de configuration définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se trouvent dans le groupe de sections `<system.serviceModel>`.</span><span class="sxs-lookup"><span data-stu-id="f9df9-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f9df9-105"> la configuration d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9df9-105"> how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="f9df9-106">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="f9df9-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="f9df9-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f9df9-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="f9df9-108">Les paramètres de configuration définis par l'application sont définis dans le groupe de sections `<appSettings>`.</span><span class="sxs-lookup"><span data-stu-id="f9df9-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f9df9-109">paramètres de l’application dans les fichiers de configuration .NET, consultez [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="f9df9-109"> application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="f9df9-110">Utilisation de l'Éditeur de configuration</span><span class="sxs-lookup"><span data-stu-id="f9df9-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="f9df9-111">Le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permet aux administrateurs et aux développeurs créer et modifier les paramètres de configuration pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services à l’aide d’une interface utilisateur graphique.</span><span class="sxs-lookup"><span data-stu-id="f9df9-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="f9df9-112">Cet outil vous permet de gérer les paramètres de liaison, comportement, service et diagnostic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans modifier directement les fichiers de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="f9df9-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="f9df9-113">Modification des fichiers de configuration dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9df9-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="f9df9-114">Pour modifier le fichier de configuration d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projet de service dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], avec le bouton droit dessus dans **l’Explorateur de solutions** et choisissez la **modifier la configuration WCF** élément de menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f9df9-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="f9df9-115">Cette opération lance le [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f9df9-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9df9-116">Si vous modifiez le fichier de configuration d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projet de Service Web dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] par dessus dans **l’Explorateur de solutions**, notez que le **modifier la configuration WCF** élément de menu contextuel est manquant .</span><span class="sxs-lookup"><span data-stu-id="f9df9-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="f9df9-117">Pour résoudre ce problème, cliquez sur le **outils** menu, puis choisissez **éditeur de configuration de Service WCF**.</span><span class="sxs-lookup"><span data-stu-id="f9df9-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="f9df9-118">Après cela, vous pouvez cliquez sur un fichier de configuration et utiliser le **modifier la configuration WCF** élément de menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f9df9-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9df9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9df9-119">See Also</span></span>  
 [<span data-ttu-id="f9df9-120">Outil Éditeur de configuration (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="f9df9-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="f9df9-121">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="f9df9-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="f9df9-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f9df9-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
