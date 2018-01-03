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
ms.workload: dotnet
ms.openlocfilehash: 9feb4553b1b9e013c5c299d867d74499a09e1434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Compatibilité de la stratégie de sécurité d'accès du code et migration
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 La partie stratégie de la sécurité d'accès du code (CAS, Code Access Security) est devenue obsolète dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Par conséquent, vous pouvez rencontrer des avertissements de compilation et des exceptions runtime si vous appelez des membres et les types de stratégie obsolètes [explicitement](#explicit_use) ou [implicitement](#implicit_use) (via d’autres types et les membres).  
  
 Vous pouvez éviter les avertissements et les erreurs comme suit :  
  
-   [Migration](#migration) à la [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] remplacement des appels obsolètes.  
  
     \- ou -  
  
-   À l’aide de la [élément de configuration < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) adopter le comportement de stratégie CAS hérité.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Utilisation explicite](#explicit_use)  
  
-   [Utilisation implicite](#implicit_use)  
  
-   [Erreurs et avertissements](#errors_and_warnings)  
  
-   [Migration : Remplacement des appels obsolètes](#migration)  
  
-   [Compatibilité : Utilisation de l’Option de stratégie CAS héritée](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Utilisation explicite  
 Les membres qui manipulent directement la stratégie de sécurité ou nécessitent la stratégie CAS en mode bac à sable (sandbox) sont obsolètes et généreront des erreurs par défaut.  
  
 En voici quelques exemples :  
  
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
## <a name="implicit-use"></a>Utilisation implicite  
 Plusieurs surcharges de chargement d'assembly génèrent des erreurs du fait de leur utilisation implicite de stratégie CAS. Ces surcharges prennent un paramètre <xref:System.Security.Policy.Evidence> utilisé pour résoudre la stratégie CAS et fournissent un jeu d'autorisations pour un assembly.  
  
 Voici quelques exemples. Les surcharges obsolètes sont celles qui prennent <xref:System.Security.Policy.Evidence> comme paramètre :  
  
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
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 Les types et membres obsolètes produisent les messages d'erreur suivants quand ils sont utilisés. Notez que le type <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> lui-même n'est pas obsolète.  
  
 Avertissement au moment de la compilation :  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Exceptions runtime :  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migration : remplacement des appels obsolètes  
  
### <a name="determining-an-assemblys-trust-level"></a>Détermination du niveau de confiance d'un assembly  
 La stratégie CAS est souvent utilisée pour déterminer le jeu d'autorisations ou le niveau de confiance d'un assembly ou d'un domaine d'application. Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose les propriétés utiles suivantes qui n'ont pas besoin de résoudre la stratégie de sécurité :  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Utilisation de bac à sable (sandbox) pour les domaines d'application  
 La méthode <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> est généralement utilisée pour la mise en bac à sable (sandbox) des assemblys dans un domaine d'application. Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose les membres qui n’ont pas à utiliser <xref:System.Security.Policy.PolicyLevel> à cet effet. Pour plus d’informations, consultez [Comment : exécuter Partially Trusted Code dans un bac à sable](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Détermination d'un jeu d'autorisations sécurisé ou raisonnable pour le code d'un niveau de confiance partiel  
 Les hôtes doivent souvent déterminer les autorisations qui sont appropriées pour l'utilisation de bacs à sable (sandbox) pour le code hébergé. Avant du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la stratégie CAS fourni pour ce faire la <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> (méthode). En remplacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fournit le <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> (méthode), qui retourne un autorisations standard sécurisé défini pour les preuves fournies.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scénarios autres que le mode bac à sable (sandbox) : surcharges pour les chargements d'assemblys  
 La raison de l'utilisation d'une surcharge de chargement d'assembly peut être de recourir à des paramètres qui ne sont pas autrement disponibles, au lieu d'utiliser le sandbox pour l'assembly. En commençant par le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], les surcharges de chargement d’assembly qui ne nécessitent pas une <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> comme paramètre un objet, par exemple, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, activer ce scénario.  
  
 Si vous voulez utiliser un bac à sable (sandbox) pour un assembly, utilisez la surcharge <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Compatibilité : utilisation de l'option de stratégie CAS héritée  
 Le [élément de configuration < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) vous permet de spécifier qu’un processus ou une bibliothèque utilise la stratégie CAS héritée. Quand vous activez cet élément, les surcharges de stratégie et de preuve fonctionnent comme dans les versions antérieures du Framework.  
  
> [!NOTE]
>  Le comportement de la stratégie CAS est spécifié par version du runtime ; la modification de la stratégie CAS pour une version du runtime n'affecte donc pas la stratégie CAS d'une autre version.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
