---
title: "Comment : spécifier le contexte de sécurité des services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 9ce65358f6d63414dbe6798d3cc2464ee2741980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="ab9f7-102">Comment : spécifier le contexte de sécurité des services</span><span class="sxs-lookup"><span data-stu-id="ab9f7-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="ab9f7-103">Par défaut, les services s’exécutent dans un contexte de sécurité autre que celle de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="ab9f7-104">Les services s’exécutés dans le contexte du compte système par défaut, appelée `LocalSystem`, ce qui leur donne différents privilèges d’accès aux ressources système que l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="ab9f7-105">Vous pouvez modifier ce comportement pour spécifier un autre compte d’utilisateur sous lequel votre service doit s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="ab9f7-106">Vous définissez le contexte de sécurité en manipulant le <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> propriété du processus dans lequel le service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="ab9f7-107">Cette propriété vous permet de définir le service à un des quatre types de comptes :</span><span class="sxs-lookup"><span data-stu-id="ab9f7-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="ab9f7-108">`User`, ce qui entraîne le système demande un nom d’utilisateur valide et un mot de passe lorsque le service est installé et s’exécute dans le contexte d’un compte spécifié par un utilisateur unique sur le réseau ;</span><span class="sxs-lookup"><span data-stu-id="ab9f7-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="ab9f7-109">`LocalService`, qui s’exécute dans le contexte d’un compte qui agit comme un utilisateur non privilégié sur l’ordinateur local et présente des informations d’identification anonymes à tout serveur distant ;</span><span class="sxs-lookup"><span data-stu-id="ab9f7-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="ab9f7-110">`LocalSystem`, qui s’exécute dans le contexte d’un compte qui fournit des privilèges locaux étendus et présente les informations d’identification de l’ordinateur à tout serveur distant ;</span><span class="sxs-lookup"><span data-stu-id="ab9f7-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="ab9f7-111">`NetworkService`, qui s’exécute dans le contexte d’un compte qui agit comme un utilisateur non privilégié sur l’ordinateur local et présente des informations d’identification de l’ordinateur à tout serveur distant.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="ab9f7-112">Pour plus d’informations, consultez l’énumération <xref:System.ServiceProcess.ServiceAccount>.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="ab9f7-113">Pour spécifier le contexte de sécurité pour un service</span><span class="sxs-lookup"><span data-stu-id="ab9f7-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="ab9f7-114">Après avoir créé votre service, ajoutez les programmes d’installation nécessaires pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="ab9f7-115">Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ab9f7-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="ab9f7-116">Dans le concepteur, accédez à la `ProjectInstaller` classe, puis cliquez sur le programme d’installation du processus de service pour le service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab9f7-117">Pour chaque application de service, il existe au moins deux composants d’installation dans le `ProjectInstaller` classe : un qui installe les processus pour tous les services dans le projet et un programme d’installation pour chaque service de l’application.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="ab9f7-118">Dans ce cas, vous souhaitez sélectionner <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="ab9f7-119">Dans le **propriétés** , configurez la <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="ab9f7-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9f7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab9f7-120">See Also</span></span>  
 [<span data-ttu-id="ab9f7-121">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="ab9f7-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="ab9f7-122">Guide pratique pour ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="ab9f7-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="ab9f7-123">Guide pratique pour créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="ab9f7-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
