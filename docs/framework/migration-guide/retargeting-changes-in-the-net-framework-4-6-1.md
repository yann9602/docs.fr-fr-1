---
title: "Modifications du reciblage dans le .NET Framework 4.6.1 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0adc4a6cae566b6a15c5fa492620abb74b47335b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-461"></a>Modifications du reciblage dans le .NET Framework 4.6.1
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Sauf indication contraire, ces modifications n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclut des modifications de reciblage dans les domaines suivants :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [Contrats de code](#Contracts)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="Core"></a>   
## <a name="core"></a>Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>|Pour les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures, le caractère de séparateur de chemin n’est plus une barre oblique inverse (« \\ »), mais une barre oblique (« / ») dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A> des objets <xref:System.IO.Compression.ZipArchiveEntry> créés par les surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>.|L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.<br /><br /> Toutefois, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures peuvent choisir de ne pas adhérer à ce comportement. Pour plus d’informations, consultez [Atténuation : Séparateur de chemin ZipArchiveEntry.FullName](../../../docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|Cas limite|  
  
<a name="Contracts"></a>   
## <a name="code-contracts"></a>Contrats de code  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=fullName> et <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=fullName>, et les appels à <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>|Pour les applications qui ciblent le .NET Framework 4.6.1, le module de réécriture émet l’avertissement CC1036 du compilateur : « Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method... ».|Il s’agit d’un avertissement du compilateur, plutôt que d’une erreur du compilateur.<br /><br /> Ce comportement est abordé dans le [problème 339](https://github.com/Microsoft/CodeContracts/issues/339), sur le site GitHub. Pour éviter cet avertissement, vous pouvez télécharger et compiler une version mise à jour du code source pour les outils Code Contracts, sur le site [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Des informations sur le téléchargement se trouvent au bas de la page.|Mineur|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation"></a>Windows Communication Foundation  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> (espace de noms <xref:System.IdentityModel.Claims>)|Dans les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], si un jeu de revendications X509 est initialisé à partir d’un certificat dont le champ SAN a plusieurs entrées DNS, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tente de faire correspondre l’argument `claimType` avec toutes les entrées DNS.<br /><br /> Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tente de faire correspondre l’argument `claimType` avec la dernière entrée DNS.|Ce changement affecte toutes les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Les applications qui ciblent des versions antérieures de .NET Framework ne sont pas affectées.<br /><br /> Toutefois, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent choisir de ne pas adhérer à ce comportement. En outre, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], peuvent choisir d’adhérer à ce comportement. Pour plus d’informations, consultez [Atténuation : X509CertificateClaimSet.FindClaims (méthode)](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|Mineur|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> (espace de noms <xref:System.Windows.Forms>)|Dans les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], une implémentation personnalisée <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> peut filtrer en toute sécurité les messages lorsque la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée si l’implémentation <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> :<br /><br /> <ul><li>Effectue l’une ou actions suivantes ou les deux :<br /><br /> <ul><li>Ajoute un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</li><li>Supprime un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .</li></ul></li><li>**Et** pompe les messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.</li></ul><br /> Dans les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, de telles implémentations peuvent, dans certains cas, lever une exception <xref:System.IndexOutOfRangeException> lorsque la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée.|Ce changement affecte toutes les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Les applications qui ciblent des versions antérieures de .NET Framework ne sont pas affectées.<br /><br /> Toutefois, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent choisir de ne pas adhérer à ce comportement. En outre, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], peuvent choisir d’adhérer à ce comportement. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|Cas limite|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications dans la version 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
