---
title: '&lt;loadFromRemoteSources&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b42405a0faf721c46476aadaa0cff8163883c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="80ca7-102">&lt;loadFromRemoteSources&gt; Element</span><span class="sxs-lookup"><span data-stu-id="80ca7-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="80ca7-103">Spécifie si les assemblys à partir de sources distantes doivent se voir accorder une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ca7-104">Si vous avez été redirigé vers cette rubrique en raison d’un message d’erreur dans la liste d’erreurs de projet Visual Studio ou une erreur de build, consultez [Comment : utiliser un Assembly à partir du Web dans Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span><span class="sxs-lookup"><span data-stu-id="80ca7-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="80ca7-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="80ca7-105">\<configuration></span></span>  
<span data-ttu-id="80ca7-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="80ca7-106">\<runtime></span></span>  
<span data-ttu-id="80ca7-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="80ca7-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ca7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80ca7-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80ca7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="80ca7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="80ca7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="80ca7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80ca7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="80ca7-111">Attributes</span></span>  
  
|<span data-ttu-id="80ca7-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="80ca7-112">Attribute</span></span>|<span data-ttu-id="80ca7-113">Description</span><span class="sxs-lookup"><span data-stu-id="80ca7-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="80ca7-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="80ca7-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="80ca7-115">Spécifie si un assembly est chargé à partir de sources distantes doit-elle se voir accorder une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="80ca7-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="80ca7-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="80ca7-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="80ca7-117">Value</span></span>|<span data-ttu-id="80ca7-118">Description</span><span class="sxs-lookup"><span data-stu-id="80ca7-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="80ca7-119">N’accordez pas une confiance totale aux applications à partir de sources distantes.</span><span class="sxs-lookup"><span data-stu-id="80ca7-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="80ca7-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="80ca7-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="80ca7-121">Accorder une confiance totale aux applications à partir de sources distantes.</span><span class="sxs-lookup"><span data-stu-id="80ca7-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80ca7-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="80ca7-122">Child Elements</span></span>  
 <span data-ttu-id="80ca7-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="80ca7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80ca7-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="80ca7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="80ca7-125">Élément</span><span class="sxs-lookup"><span data-stu-id="80ca7-125">Element</span></span>|<span data-ttu-id="80ca7-126">Description</span><span class="sxs-lookup"><span data-stu-id="80ca7-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="80ca7-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80ca7-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="80ca7-128">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="80ca7-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ca7-129">Notes</span><span class="sxs-lookup"><span data-stu-id="80ca7-129">Remarks</span></span>  
 <span data-ttu-id="80ca7-130">Dans le .NET Framework version 3.5 et les versions antérieures, si vous avez chargé un assembly à partir d’un emplacement distant, l’assembly s’exécute une confiance partielle avec un jeu d’autorisations qui dépendaient de la zone dans laquelle il a été chargé.</span><span class="sxs-lookup"><span data-stu-id="80ca7-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="80ca7-131">Par exemple, si vous avez chargé un assembly à partir d’un site Web, il a été chargé dans la zone Internet et accordé le jeu d’autorisations Internet.</span><span class="sxs-lookup"><span data-stu-id="80ca7-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="80ca7-132">En d’autres termes, elle est exécutée dans un bac à sable Internet.</span><span class="sxs-lookup"><span data-stu-id="80ca7-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="80ca7-133">Si vous essayez d’exécuter cet assembly dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et versions ultérieures, une exception est levée ; vous devez soit créer explicitement un bac à sable pour l’assembly (consultez [Comment : exécuter Partially Trusted Code dans un bac à sable](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ou l’exécuter en mode confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="80ca7-134">Le `<loadFromRemoteSources>` élément vous permet de spécifier que les assemblys qui auraient été exécutées de confiance partiel dans les versions antérieures du .NET Framework doivent être exécutées entièrement confiance dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="80ca7-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="80ca7-135">Par défaut, les assemblys à distance ne s’exécutent pas dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="80ca7-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="80ca7-136">Pour exécuter un assembly distant, vous devez l’exécuter avec une confiance totale ou créer un bac à sable <xref:System.AppDomain> dans pour son exécution.</span><span class="sxs-lookup"><span data-stu-id="80ca7-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ca7-137">Dans le [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblys sur des partages de réseau local sont exécutées avec une confiance totale par défaut ; vous n’avez pas à activer le `<loadFromRemoteSources>` élément.</span><span class="sxs-lookup"><span data-stu-id="80ca7-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ca7-138">Si une application a été copiée à partir du web, il est signalé par Windows comme étant une application web, même s’il se trouve sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="80ca7-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="80ca7-139">Vous pouvez modifier cette désignation en modifiant les propriétés du fichier, ou vous pouvez utiliser la `<loadFromRemoteSources>` élément à accorder à l’assembly de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="80ca7-140">En guise d’alternative, vous pouvez utiliser la <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> méthode pour charger un assembly local que le système d’exploitation a signalé comme ayant été chargé à partir du web.</span><span class="sxs-lookup"><span data-stu-id="80ca7-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="80ca7-141">Le `enabled` d’attribut pour cet élément est efficace uniquement lorsque la sécurité d’accès du code (CAS) est désactivée.</span><span class="sxs-lookup"><span data-stu-id="80ca7-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="80ca7-142">Par défaut, la stratégie CAS est désactivée dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="80ca7-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="80ca7-143">Si vous définissez `enabled` à `true`, applications distantes sont de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="80ca7-144">Si `<loadFromRemoteSources>``enabled` n’est pas définie `true`, une exception est levée dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="80ca7-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="80ca7-145">Le comportement de bac à sable du domaine actuel est différent de son comportement dans le [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80ca7-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="80ca7-146">Cela nécessite la stratégie CAS doit être désactivée et le domaine actuel, ne pas à sable (sandbox).</span><span class="sxs-lookup"><span data-stu-id="80ca7-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="80ca7-147">L’assembly en cours de chargement n’est pas à partir de la `MyComputer` zone.</span><span class="sxs-lookup"><span data-stu-id="80ca7-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ca7-148">Vous risquez d’obtenir un <xref:System.IO.FileLoadException> dans une application Windows Virtual PC lorsque vous essayez de charger un fichier à partir des dossiers liés sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="80ca7-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="80ca7-149">Cette erreur peut également se produire lorsque vous essayez de charger un fichier à partir d’un dossier lié via [Services Bureau à distance](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span><span class="sxs-lookup"><span data-stu-id="80ca7-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="80ca7-150">Pour éviter l’exception, définissez `enabled` à `true`.</span><span class="sxs-lookup"><span data-stu-id="80ca7-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="80ca7-151">Définition de la `<loadFromRemoteSources>` élément `true` empêche cette exception ne soit levée.</span><span class="sxs-lookup"><span data-stu-id="80ca7-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="80ca7-152">Il permet de spécifier que vous ne comptez pas sur le common language runtime pour le bac à sable les assemblys chargés pour la sécurité, et qu’ils soient autorisés à exécuter en tant qu’une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="80ca7-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="80ca7-153">Si l’assembly ne doit pas s’exécuter en mode confiance totale, ne définissez pas cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="80ca7-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="80ca7-154">Au lieu de cela, créez un bac à sable <xref:System.AppDomain> dans lequel charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="80ca7-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="80ca7-155">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="80ca7-155">Configuration File</span></span>  
 <span data-ttu-id="80ca7-156">Cet élément est généralement utilisé dans le fichier de configuration d’application, mais il peut être utilisé dans d’autres fichiers de configuration en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="80ca7-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="80ca7-157">Pour plus d’informations, consultez l’article [plus implicite utilise de la stratégie CAS : loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) dans le blog de sécurité .NET.</span><span class="sxs-lookup"><span data-stu-id="80ca7-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ca7-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="80ca7-158">Example</span></span>  
 <span data-ttu-id="80ca7-159">L’exemple suivant montre comment accorder une confiance totale aux applications à partir de sources distantes.</span><span class="sxs-lookup"><span data-stu-id="80ca7-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80ca7-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80ca7-160">See Also</span></span>  
 [<span data-ttu-id="80ca7-161">Utilise plus implicite de stratégie CAS : loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="80ca7-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="80ca7-162">Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="80ca7-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="80ca7-163">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="80ca7-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="80ca7-164">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="80ca7-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
