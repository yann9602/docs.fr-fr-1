---
title: "Compatibilit&#233; de la strat&#233;gie de s&#233;curit&#233; d&#39;acc&#232;s du code et migration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "migration des stratégies CLR"
  - "migration des stratégies, compatibilité"
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Compatibilit&#233; de la strat&#233;gie de s&#233;curit&#233; d&#39;acc&#232;s du code et migration
La partie stratégie de la sécurité d'accès du code \(CAS, Code Access Security\) est devenue obsolète dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].  Vous pouvez donc rencontrer des avertissements de compilation et des exceptions runtime si vous appelez des types et membres de stratégie obsolètes [explicitement](#explicit_use) ou [implicitement](#implicit_use) \(via d'autres types et membres\).  
  
 Vous pouvez éviter les avertissements et les erreurs comme suit :  
  
-   [En migrant](#migration) vers les remplacements [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] des appels obsolètes.  
  
     ou  
  
-   À l'aide de l'[élément de configuration \<NetFx40\_LegacySecurityPolicy\>](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pour utiliser le comportement de stratégie CAS hérité.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Utilisation explicite](#explicit_use)  
  
-   [Utilisation implicite](#implicit_use)  
  
-   [Erreurs et avertissements](#errors_and_warnings)  
  
-   [Migration : remplacement des appels obsolètes](#migration)  
  
-   [Compatibilité : utilisation de l'option de stratégie CAS héritée](#compatibility)  
  
> [!CAUTION]
>  Sécurité d'accès du code et code d'un niveau de confiance partiel  
>   
>  Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code \(CAS\) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.  La sécurité d'accès du code dans .NET Framework ne doit pas être utilisée comme limite de sécurité avec du code d'un niveau de confiance partiel, notamment du code d'origine inconnue.  Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.  
>   
>  Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.  
  
<a name="explicit_use"></a>   
## Utilisation explicite  
 Les membres qui manipulent directement la stratégie de sécurité ou nécessitent la stratégie CAS en mode bac à sable \(sandbox\) sont obsolètes et généreront des erreurs par défaut.  
  
 En voici quelques exemples :  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=fullName>  
  
<a name="implicit_use"></a>   
## Utilisation implicite  
 Plusieurs surcharges de chargement d'assembly génèrent des erreurs du fait de leur utilisation implicite de stratégie CAS.  Ces surcharges prennent un paramètre <xref:System.Security.Policy.Evidence> utilisé pour résoudre la stratégie CAS et fournissent un jeu d'autorisations pour un assembly.  
  
 Voici quelques exemples.  Les surcharges obsolètes sont celles qui prennent <xref:System.Security.Policy.Evidence> comme paramètre :  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
<a name="errors_and_warnings"></a>   
## Erreurs et avertissements  
 Les types et membres obsolètes produisent les messages d'erreur suivants quand ils sont utilisés.  Notez que le type <xref:System.Security.Policy.Evidence?displayProperty=fullName> lui\-même n'est pas obsolète.  
  
 Avertissement au moment de la compilation :  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework.  Please use <suggested alternate API>.  See <link> for more information.'`  
  
 Exceptions runtime :  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## Migration : remplacement des appels obsolètes  
  
### Détermination du niveau de confiance d'un assembly  
 La stratégie CAS est souvent utilisée pour déterminer le jeu d'autorisations ou le niveau de confiance d'un assembly ou d'un domaine d'application.  Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose les propriétés utiles suivantes qui n'ont pas besoin de résoudre la stratégie de sécurité :  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=fullName>  
  
### Utilisation de bac à sable \(sandbox\) pour les domaines d'application  
 La méthode <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName> est généralement utilisée pour la mise en bac à sable \(sandbox\) des assemblys dans un domaine d'application.  Le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expose des membres qui n'ont pas besoin d'utiliser <xref:System.Security.Policy.PolicyLevel> à cet effet. Pour plus d'informations, consultez [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### Détermination d'un jeu d'autorisations sécurisé ou raisonnable pour le code d'un niveau de confiance partiel  
 Les hôtes doivent souvent déterminer les autorisations qui sont appropriées pour l'utilisation de bacs à sable \(sandbox\) pour le code hébergé.  Avant le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la stratégie CAS permettait de le faire avec la méthode <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName>.  À la place, le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fournit la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName>, qui retourne un jeu d'autorisations standard sécurisé pour les preuves fournies.  
  
### Scénarios autres que le mode bac à sable \(sandbox\) : surcharges pour les chargements d'assemblys  
 La raison de l'utilisation d'une surcharge de chargement d'assembly peut être de recourir à des paramètres qui ne sont pas autrement disponibles, au lieu d'utiliser le sandbox pour l'assembly.  À partir du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], les surcharges de chargement d'assembly qui ne nécessitent pas d'objet <xref:System.Security.Policy.Evidence?displayProperty=fullName> comme paramètre, par exemple [AppDomain.ExecuteAssembly\(String, String\[\], Byte\<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=fullName>, permettent ce scénario.  
  
 Si vous voulez utiliser un bac à sable \(sandbox\) pour un assembly, utilisez la surcharge [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName>.  
  
<a name="compatibility"></a>   
## Compatibilité : utilisation de l'option de stratégie CAS héritée  
 L'[élément de configuration \<NetFx40\_LegacySecurityPolicy\>](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) vous permet de spécifier qu'un processus ou une bibliothèque utilise la stratégie CAS héritée.  Quand vous activez cet élément, les surcharges de stratégie et de preuve fonctionnent comme dans les versions antérieures du Framework.  
  
> [!NOTE]
>  Le comportement de la stratégie CAS est spécifié par version du runtime ; la modification de la stratégie CAS pour une version du runtime n'affecte donc pas la stratégie CAS d'une autre version.  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)