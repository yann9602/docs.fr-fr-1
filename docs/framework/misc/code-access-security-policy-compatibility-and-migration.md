---
title: "Compatibilité de la stratégie de sécurité d'accès du code et migration"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11c64d3ece454e95adfc41c7d89913e9ce7363dc
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="b7c71-102">Compatibilité de la stratégie de sécurité d'accès du code et migration</span><span class="sxs-lookup"><span data-stu-id="b7c71-102">Code Access Security Policy Compatibility and Migration</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="b7c71-103">La partie stratégie de la sécurité d'accès du code (CAS, Code Access Security) est devenue obsolète dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7c71-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b7c71-104">Par conséquent, vous pouvez rencontrer des avertissements de compilation et des exceptions runtime si vous appelez des membres et les types de stratégie obsolètes [explicitement](#explicit_use) ou [implicitement](#implicit_use) (via d’autres types et les membres).</span><span class="sxs-lookup"><span data-stu-id="b7c71-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>  
  
 <span data-ttu-id="b7c71-105">Vous pouvez éviter les avertissements et les erreurs comme suit :</span><span class="sxs-lookup"><span data-stu-id="b7c71-105">You can avoid the warnings and errors by either:</span></span>  
  
-   <span data-ttu-id="b7c71-106">[Migration](#migration) à la [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] remplacement des appels obsolètes.</span><span class="sxs-lookup"><span data-stu-id="b7c71-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>  
  
     <span data-ttu-id="b7c71-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="b7c71-107">\- or -</span></span>  
  
-   <span data-ttu-id="b7c71-108">À l’aide de la [élément de configuration < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) adopter le comportement de stratégie CAS hérité.</span><span class="sxs-lookup"><span data-stu-id="b7c71-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>  
  
 <span data-ttu-id="b7c71-109">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7c71-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="b7c71-110">Utilisation explicite</span><span class="sxs-lookup"><span data-stu-id="b7c71-110">Explicit Use</span></span>](#explicit_use)  
  
-   [<span data-ttu-id="b7c71-111">Utilisation implicite</span><span class="sxs-lookup"><span data-stu-id="b7c71-111">Implicit Use</span></span>](#implicit_use)  
  
-   [<span data-ttu-id="b7c71-112">Erreurs et avertissements</span><span class="sxs-lookup"><span data-stu-id="b7c71-112">Errors and Warnings</span></span>](#errors_and_warnings)  
  
-   [<span data-ttu-id="b7c71-113">Migration : Remplacement des appels obsolètes</span><span class="sxs-lookup"><span data-stu-id="b7c71-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)  
  
-   [<span data-ttu-id="b7c71-114">Compatibilité : Utilisation de l’Option de stratégie CAS héritée</span><span class="sxs-lookup"><span data-stu-id="b7c71-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a><span data-ttu-id="b7c71-115">Utilisation explicite</span><span class="sxs-lookup"><span data-stu-id="b7c71-115">Explicit Use</span></span>  
 <span data-ttu-id="b7c71-116">Les membres qui manipulent directement la stratégie de sécurité ou nécessitent la stratégie CAS en mode bac à sable (sandbox) sont obsolètes et généreront des erreurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="b7c71-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>  
  
 <span data-ttu-id="b7c71-117">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="b7c71-117">Examples of these are:</span></span>  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a><span data-ttu-id="b7c71-118">Utilisation implicite</span><span class="sxs-lookup"><span data-stu-id="b7c71-118">Implicit Use</span></span>  
 <span data-ttu-id="b7c71-119">Plusieurs surcharges de chargement d'assembly génèrent des erreurs du fait de leur utilisation implicite de stratégie CAS.</span><span class="sxs-lookup"><span data-stu-id="b7c71-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="b7c71-120">Ces surcharges prennent un paramètre <xref:System.Security.Policy.Evidence> utilisé pour résoudre la stratégie CAS et fournissent un jeu d'autorisations pour un assembly.</span><span class="sxs-lookup"><span data-stu-id="b7c71-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>  
  
 <span data-ttu-id="b7c71-121">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="b7c71-121">Here are some examples.</span></span> <span data-ttu-id="b7c71-122">Les surcharges obsolètes sont celles qui prennent <xref:System.Security.Policy.Evidence> comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="b7c71-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a><span data-ttu-id="b7c71-123">Erreurs et avertissements</span><span class="sxs-lookup"><span data-stu-id="b7c71-123">Errors and Warnings</span></span>  
 <span data-ttu-id="b7c71-124">Les types et membres obsolètes produisent les messages d'erreur suivants quand ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="b7c71-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="b7c71-125">Notez que le type <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> lui-même n'est pas obsolète.</span><span class="sxs-lookup"><span data-stu-id="b7c71-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>  
  
 <span data-ttu-id="b7c71-126">Avertissement au moment de la compilation :</span><span class="sxs-lookup"><span data-stu-id="b7c71-126">Compile-time warning:</span></span>  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 <span data-ttu-id="b7c71-127">Exceptions runtime :</span><span class="sxs-lookup"><span data-stu-id="b7c71-127">Run-time exception:</span></span>  
  
 <span data-ttu-id="b7c71-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="b7c71-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="b7c71-129">Migration : remplacement des appels obsolètes</span><span class="sxs-lookup"><span data-stu-id="b7c71-129">Migration: Replacement for Obsolete Calls</span></span>  
  
### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="b7c71-130">Détermination du niveau de confiance d'un assembly</span><span class="sxs-lookup"><span data-stu-id="b7c71-130">Determining an Assembly’s Trust Level</span></span>  
 <span data-ttu-id="b7c71-131">La stratégie CAS est souvent utilisée pour déterminer le jeu d'autorisations ou le niveau de confiance d'un assembly ou d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="b7c71-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="b7c71-132">Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose les propriétés utiles suivantes qui n'ont pas besoin de résoudre la stratégie de sécurité :</span><span class="sxs-lookup"><span data-stu-id="b7c71-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a><span data-ttu-id="b7c71-133">Utilisation de bac à sable (sandbox) pour les domaines d'application</span><span class="sxs-lookup"><span data-stu-id="b7c71-133">Application Domain Sandboxing</span></span>  
 <span data-ttu-id="b7c71-134">La méthode <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> est généralement utilisée pour la mise en bac à sable (sandbox) des assemblys dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="b7c71-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="b7c71-135">Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose les membres qui n’ont pas à utiliser <xref:System.Security.Policy.PolicyLevel> à cet effet.</span><span class="sxs-lookup"><span data-stu-id="b7c71-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="b7c71-136">Pour plus d’informations, consultez [Comment : exécuter Partially Trusted Code dans un bac à sable](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="b7c71-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="b7c71-137">Détermination d'un jeu d'autorisations sécurisé ou raisonnable pour le code d'un niveau de confiance partiel</span><span class="sxs-lookup"><span data-stu-id="b7c71-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>  
 <span data-ttu-id="b7c71-138">Les hôtes doivent souvent déterminer les autorisations qui sont appropriées pour l'utilisation de bacs à sable (sandbox) pour le code hébergé.</span><span class="sxs-lookup"><span data-stu-id="b7c71-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="b7c71-139">Avant du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la stratégie CAS fourni pour ce faire la <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b7c71-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7c71-140">En remplacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fournit le <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> (méthode), qui retourne un autorisations standard sécurisé défini pour les preuves fournies.</span><span class="sxs-lookup"><span data-stu-id="b7c71-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="b7c71-141">Scénarios autres que le mode bac à sable (sandbox) : surcharges pour les chargements d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b7c71-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>  
 <span data-ttu-id="b7c71-142">La raison de l'utilisation d'une surcharge de chargement d'assembly peut être de recourir à des paramètres qui ne sont pas autrement disponibles, au lieu d'utiliser le sandbox pour l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7c71-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="b7c71-143">En commençant par le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], les surcharges de chargement d’assembly qui ne nécessitent pas une <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> comme paramètre un objet, par exemple, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, activer ce scénario.</span><span class="sxs-lookup"><span data-stu-id="b7c71-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>  
  
 <span data-ttu-id="b7c71-144">Si vous voulez utiliser un bac à sable (sandbox) pour un assembly, utilisez la surcharge <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7c71-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="b7c71-145">Compatibilité : utilisation de l'option de stratégie CAS héritée</span><span class="sxs-lookup"><span data-stu-id="b7c71-145">Compatibility: Using the CAS Policy Legacy Option</span></span>  
 <span data-ttu-id="b7c71-146">Le [élément de configuration < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) vous permet de spécifier qu’un processus ou une bibliothèque utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="b7c71-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="b7c71-147">Quand vous activez cet élément, les surcharges de stratégie et de preuve fonctionnent comme dans les versions antérieures du Framework.</span><span class="sxs-lookup"><span data-stu-id="b7c71-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7c71-148">Le comportement de la stratégie CAS est spécifié par version du runtime ; la modification de la stratégie CAS pour une version du runtime n'affecte donc pas la stratégie CAS d'une autre version.</span><span class="sxs-lookup"><span data-stu-id="b7c71-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7c71-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7c71-149">See Also</span></span>  
 [<span data-ttu-id="b7c71-150">Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="b7c71-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="b7c71-151">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="b7c71-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
