---
title: "Modification du reciblage dans le .NET Framework 4.6 | Microsoft Docs"
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
- retargeting changes, .NET Framework 4.6
- application compatibility
ms.assetid: fa849255-f90f-4bf1-b0ff-b173c12110d7
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 19ad80233a79a4fdef89550696c1c3d33e14b355
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-46"></a>Reciblage des modifications dans le .NET Framework 4.6
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Sauf indication contraire, ces modifications n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].  
  
 Le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] inclut des modifications de reciblage dans les domaines suivants :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [ASP.NET](#ASP)  
  
-   [Mise en réseau](#Net)  
  
-   [Windows Communications Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>, et les opérations asynchrones basées sur les tâches avec <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>|Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et versions ultérieures, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont stockés dans le <xref:System.Threading.ExecutionContext> d’un thread, qui transite via des opérations asynchrones.|Les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> seront reflétées dans les tâches asynchrones qui seront lancées par la suite. Pour plus d’informations, consultez [Atténuation : culture et opérations asynchrones](../../../docs/framework/migration-guide/mitigation-culture-and-asynchronous-operations.md).|Mineur|  
  
<a name="ASP"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> avec une valeur `tagKey` de <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName>|En conformité avec la norme HTML, la méthode <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> affiche désormais <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> comme une balise non fermante dans une réponse HTML.|L’étiquette BR génère désormais un saut de ligne. Auparavant, elle générait deux sauts de ligne.<br /><br /> Les applications qui dépendent de la balise `<BR>` pour produire deux sauts de ligne peuvent restaurer le comportement précédent en ajoutant un appel supplémentaire à la méthode <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> avec l’argument <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName>.|Mineur|  
  
<a name="Net"></a>   
## <a name="networking"></a>Réseau  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.ServicePointManager?displayProperty=fullName> et <xref:System.Net.Security.SslStream?displayProperty=fullName>|Dans les applications qui ciblent le .NET Framework 4.6 et versions ultérieures, les classes <xref:System.Net.ServicePointManager?displayProperty=fullName> et <xref:System.Net.Security.SslStream?displayProperty=fullName> sont autorisées à utiliser l’un des trois protocoles suivants : Tls1.0, Tls1.1 et Tls 1.2.<br /><br /> Les applications qui ciblent une version antérieure du .NET Framework, même si elles s'exécutent sur le .NET Framework 4.6, ne sont pas affectées.|Ce changement affecte toutes les applications qui ciblent le .NET Framework 4.6 et qui utilisent le protocole SSL pour communiquer avec un serveur HTTPS ou un serveur socket en utilisant l’un des types suivants : <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> et <xref:System.Net.Security.SslStream>.  Pour plus d’informations, consultez [Atténuation : protocoles TLS](../../../docs/framework/migration-guide/mitigation-tls-protocols.md).|Mineur|  
  
<a name="WCF"></a>   
## <a name="windows-communications-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%2A?displayProperty=fullName>|Le <xref:System.IdentityModel.Policy.AuthorizationContext> retourné par un appel à <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> avec un argument `null``authorizationPolicies` a une nouvelle implémentation dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].|Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement. Si l’ancien comportement est nécessaire, consultez [Atténuation : AuthorizationContext par défaut](../../../docs/framework/migration-guide/mitigation-default-authorizationcontext.md).|Mineur|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName>|Dans les applications qui ciblent le .NET Framework 4.6 et versions ultérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> convertit correctement les icônes avec cadres PNG en objets <xref:System.Drawing.Bitmap>.<br /><br /> Dans les applications qui ciblent le .NET Framework 4.5.2 et versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet <xref:System.Drawing.Icon> comprend des cadres PNG.|Ce changement affecte les applications qui sont recompilées pour cibler le .NET Framework 4.6 et qui fournissent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée si un objet <xref:System.Drawing.Icon> comporte des cadres PNG. Si ce comportement n’est pas souhaitable, un commutateur de configuration rétablit le comportement précédent. Pour plus d’informations, consultez [Atténuation : cadres PNG dans les objets Icon](../../../docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|Mineur|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>|Dans les applications qui ciblent le .NET Framework 4.6 et 4.6.1, les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> au sein d’un <xref:System.Windows.Threading.Dispatcher> seront perdues à la fin de l’opération de répartiteur. De même, les modifications apportées à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en dehors d’une opération de répartiteur peuvent ne pas être reflétées au moment où s’exécute l’opération.|Les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> peuvent ne pas être transmises entre les rappels d’interface utilisateur de WPF et un autre code de l’application WPF. Pour plus d’informations, consultez [Atténuation : culture et opérations de répartiteur dans les applications WPF](../../../docs/framework/migration-guide/mitigation-culture-and-dispatcher-operations-in-wpf-apps.md).|Mineur|  
|Arrondi de disposition à DPI élevé|La façon dont les marges sont arrondies, les bordures et l'arrière-plan ont changé.|La disposition des contrôles WPF peut varier légèrement. Pour plus d’informations, consultez [Atténuation : disposition WPF](../../../docs/framework/migration-guide/mitigation-wpf-layout.md).|Mineur|  
  
<a name="XML"></a>   
## <a name="xml"></a>XML  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Validation de schéma XSD|Depuis le .NET Framework 4.6, la validation de schéma XSD détecte une violation de contrainte unique si une clé composée est utilisée et qu’une clé est vide.|Consultez [Atténuation : validation du schéma XML](../../../docs/framework/migration-guide/mitigation-xml-schema-validation.md)|Mineur|  
|<xref:System.Xml.XmlWriter>|Pour les applications qui ciblent .NET Framework 4.5.2 ou des versions antérieures, l'écriture d'une paire de substitution non valide à l'aide de la gestion des stratégies de secours des exceptions ne lève pas toujours une exception.<br /><br /> Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la tentative d’écriture d’une paire de substitution non valide lève une exception <xref:System.ArgumentException>.|Les applications qui sont recompilées pour cibler [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], et qui écrivent des paires de substitution non valides, lèvent une exception dans les cas où elles ne le faisaient pas auparavant.|Cas limite|
