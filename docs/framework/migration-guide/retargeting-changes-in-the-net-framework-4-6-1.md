---
title: "Reciblage des modifications dans .NET Framework&#160;4.6.1 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Reciblage des modifications dans .NET Framework&#160;4.6.1
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Sauf indication contraire, ces modifications n'affectent pas les fichiers binaires qui ciblent une version antérieure de .NET Framework mais s'exécutent sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclut des modifications de reciblage dans les domaines suivants :  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="WCF"></a>   
## Windows Communication Foundation  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> \(espace de noms <xref:System.IdentityModel.Claims>\)|Dans les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], si un jeu de revendications X509 est initialisé à partir d’un certificat dont le champ SAN a plusieurs entrées DNS, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tente de faire correspondre l’argument `claimType` avec toutes les entrées DNS.<br /><br /> Pour les applications qui ciblent des versions antérieures de .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.|Cette modification affecte toutes les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Les applications qui ciblent des versions antérieures de .NET Framework ne sont pas affectées.<br /><br /> Toutefois, les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent ne pas adopter ce comportement. En outre, les applications qui ciblent des versions antérieures de .NET Framework mais qui s’exécutent sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent adopter ce comportement. Pour plus d'informations, consultez [Atténuation : X509CertificiateClaimSet.FindClaim \(méthode\)](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|Secondaire|  
  
<a name="WinForms"></a>   
## Windows Forms  
  
|Fonctionnalité|Modification|Impact|Portée|  
|--------------------|------------------|------------|------------|  
|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName>, méthode \(espace de noms <xref:System.Windows.Forms>\)|Dans les applications Windows Forms qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> :<br /><br /> <ul><li>Effectue l’une ou actions suivantes ou les deux :<br /><br /> <ul><li>Ajoute un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</li><li>Supprime un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .</li></ul></li><li>**Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.</li></ul><br /> Ces implémentations dans les applications Windows Forms qui ciblent des versions antérieures de .NET Framework lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée.|Cette modification affecte toutes les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Les applications qui ciblent des versions antérieures de .NET Framework ne sont pas affectées.<br /><br /> Toutefois, les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent ne pas adopter ce comportement. En outre, les applications qui ciblent des versions antérieures de .NET Framework mais qui s’exécutent sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent adopter ce comportement. Pour plus d'informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|Bord|  
  
## Voir aussi  
 [Compatibilité des applications dans la version 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)