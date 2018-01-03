---
title: Utilisation de System.Transactions dans ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caa0f8cc5b98ae50e1c9d2da716dd03eb5cb4565
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="86fd3-102">Utilisation de System.Transactions dans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="86fd3-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="86fd3-103">Cette rubrique explique comment utiliser <xref:System.Transactions> dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="86fd3-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="86fd3-104">Activation de DistributedTransactionPermission dans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="86fd3-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="86fd3-105"><xref:System.Transactions> prend en charge les appelants d’un niveau de confiance partiel et est marqué avec l’attribut **AllowPartiallyTrustedCallers** (APTCA).</span><span class="sxs-lookup"><span data-stu-id="86fd3-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="86fd3-106">Les niveaux de confiance pour les <xref:System.Transactions> sont définis d’après les types de ressource (par exemple, la mémoire système, les ressources partagées au niveau du processus, les ressources système et d’autres ressources) exposés par <xref:System.Transactions> et le niveau de confiance requis pour accéder à ces ressources.</span><span class="sxs-lookup"><span data-stu-id="86fd3-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="86fd3-107">Dans un environnement de confiance partielle, un assembly qui n’a pas un niveau de confiance totale ne peut utiliser que les transactions du domaine d’application (dans ce cas, les seules ressources protégées correspondent à la mémoire système), sauf s’il dispose de l’autorisation <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="86fd3-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="86fd3-108">L’autorisation<xref:System.Transactions.DistributedTransactionPermission> est demandée chaque fois que la gestion des transactions est remontée pour être managée par le MSDTC (Microsoft Distributed Transaction Coordinator).</span><span class="sxs-lookup"><span data-stu-id="86fd3-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="86fd3-109">Ce genre de scénario utilise des ressources au niveau du processus et, en particulier, une ressource globale servant d’espace réservé dans le journal MSDTC.</span><span class="sxs-lookup"><span data-stu-id="86fd3-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="86fd3-110">Par exemple, le composant web frontal d’une base de données ou une application qui utilise une base de donnée en tant que partie des services qu’il fournit.</span><span class="sxs-lookup"><span data-stu-id="86fd3-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="86fd3-111"> dispose de son propre jeu de niveaux de confiance et associe un jeu d’autorisations spécifique à ces niveaux de confiance via des fichiers de stratégie.</span><span class="sxs-lookup"><span data-stu-id="86fd3-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="86fd3-112">[Les fichiers de stratégie et les niveaux de confiance ASP.NET](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span><span class="sxs-lookup"><span data-stu-id="86fd3-112"> [ASP.NET Trust Levels and Policy Files](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="86fd3-113">Lors de la première installation du Kit de développement logiciel (SDK) Windows, aucun des fichiers de stratégie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] par défaut n’est associé à <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="86fd3-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="86fd3-114">Ainsi, lorsque votre transaction est remontée dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour gestion par le MSDTC, la remontée échoue avec une <xref:System.Security.SecurityException> lors de la demande de <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="86fd3-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="86fd3-115">Pour activer la remontée des transactions au sein d’un environnement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de confiance partielle, vous devez accorder l’autorisation <xref:System.Transactions.DistributedTransactionPermission> aux mêmes niveaux de confiance par défaut que ceux de l’autorisation <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="86fd3-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="86fd3-116">Vous pouvez configurer vos propres niveaux de confiance et fichier de stratégie personnalisés pour la prise en charge ou modifier les fichiers de stratégie par défaut : **Web_hightrust.config** et **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="86fd3-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="86fd3-117">Pour modifier les fichiers de stratégie, ajoutez un **SecurityClass** , élément pour les **DistributedTransactionPermission** à la **SecurityClasses** élément sous la  **PolicyLevel qui n’est** élément et ajoutez un correspondant **IPermission** élément sous le [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** pour System.Transactions.</span><span class="sxs-lookup"><span data-stu-id="86fd3-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="86fd3-118">Le fichier de configuration suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="86fd3-118">The following configuration file demonstrates this.</span></span>  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="86fd3-119"> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sur la stratégie de sécurité, consultez la page [securityPolicy élément (Schéma des paramètres ASP.NET)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span><span class="sxs-lookup"><span data-stu-id="86fd3-119"> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="86fd3-120">Compilation dynamique</span><span class="sxs-lookup"><span data-stu-id="86fd3-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="86fd3-121">Pour importer et utiliser <xref:System.Transactions> dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compilée dynamiquement lors de l’accès, insérez une référence à l’assembly <xref:System.Transactions> dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="86fd3-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="86fd3-122">Cette référence doit être ajoutée sous la section **compilation**/**assemblies** du fichier de configuration **Web.config** racine par défaut ou du fichier de configuration d’une application Web spécifique.</span><span class="sxs-lookup"><span data-stu-id="86fd3-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="86fd3-123">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="86fd3-123">The following example demonstrates this.</span></span>  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="86fd3-124"> [add, élément de assemblies pour compilation (Schéma des paramètres ASP.NET)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span><span class="sxs-lookup"><span data-stu-id="86fd3-124"> [add Element for assemblies for compilation (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fd3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86fd3-125">See Also</span></span>  
 [<span data-ttu-id="86fd3-126">Les fichiers de stratégie et les niveaux de confiance ASP.NET</span><span class="sxs-lookup"><span data-stu-id="86fd3-126">ASP.NET Trust Levels and Policy Files</span></span>](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="86fd3-127">securityPolicy, élément (schéma des paramètres ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="86fd3-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="86fd3-128">Remontée de la gestion des transactions</span><span class="sxs-lookup"><span data-stu-id="86fd3-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
