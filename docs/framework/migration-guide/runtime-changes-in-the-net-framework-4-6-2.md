---
title: "Modification du runtime dans le .NET Framework 4.6.2 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 23bf3a87-6fa1-4b5e-b92c-a39867a06e7f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: da809955776b5a5cd3776898ecc4c97db74ceb0e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-462"></a>Modifications du runtime dans le .NET Framework 4.6.2
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], des modifications ont été apportées au niveau de :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [ASP.NET](#ASP)

-   [Données](#Data)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [Signature et validation XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName><br /><br /> <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory%2A?displayProperty=fullName>|Les catégories de caractères dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] sont basées sur Unicode Version 8.0. Les versions 4.5 à 4.6.1 de .NET Framework classaient les caractères Unicode en fonction se basant sur la version 6.3 d’Unicode.<br /><br /> La comparaison de caractères et le tri ne sont pas affectés par cette modification. Pour plus d’informations, consultez la section « Chaînes et norme Unicode » de l’article <xref:System.String>.|Les catégories de caractères dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] peuvent ne pas correspondre à celles des versions antérieures de .NET Framework. Ce changement affecte principalement les syllabes Cherokee et signes de voyelle Nouveau taï-lue ainsi que les marques d’accentuation.<br /><br /> Pour répondre à cette modification, passez en revue le code et supprimez ou modifiez la logique qui varie selon des catégories de caractères Unicode codées en dur.|Mineur|  
|<xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.RSACng.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=fullName>|À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ces méthodes sont en mesure d’accéder aux clés avec des tailles de clé non standard pour les certificats RSA. Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, les tentatives d’accéder à ces clés levaient une <xref:System.Security.Cryptography.CryptographicException>.|Si une logique de gestion des exceptions s’appuie sur une <xref:System.Security.Cryptography.CryptographicException> lorsque des tailles de clé non standard sont utilisées, elle doit être supprimée.|Limité|  
|<xref:System.Security.Cryptography.RSACng.VerifyHash%2A?displayProperty=fullName>|À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette méthode renvoie `false` si une signature est mal formatée. Elle renvoie désormais `false` pour tout échec de vérification.<br /><br /> Dans [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException> si la signature proprement dite n’est pas formatée correctement.|Tout code dont l’exécution dépend de <xref:System.Security.Cryptography.CryptographicException> doit s’exécuter à la place si la validation échoue et que la méthode retourne `false`.|Mineur|  
  
## <a name="a-nameasp--aspnet"></a><a name="ASP" /> ASP.NET

|Fonctionnalité|Modification|Impact|Portée| 
|-------------|------------|------------|-----------|  
| <xref:System.Web.HttpRuntime.AppDomainApopPath%2A> | Dans .NET Framework 4.6.2, le runtime lève une <xref:System.NullReferenceException> lorsque vous récupérez une valeur <xref:System.Web.HttpRuntime.AppDomainAppPath%2A> qui inclut des caractères Null. Dans .NET Framework 4.6.1 et versions antérieures, il lève une <xref:System.ArgumentNullException>.  | Vous pouvez effectuer les opérations suivantes pour répondre à cette modification : <br/> - Gérez <xref:System.NullReferenceException> si votre application s’exécute sur .NET Framework 4.6.2. <br /> - Mettez à niveau vers .NET Framework 4.7, qui rétablit le comportement précédent et génère une <xref:System.ArgumentNullException>. | Limité |

<a name="Data"></a>   
## <a name="data"></a>Données  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Période de blocage du pool de connexions pour les bases de données Azure SQL|Pour les demandes d’ouverture de connexion pour des bases de données Azure SQL connues, la période de blocage du pool de connexions est supprimée.|Chaque nouvelle tentative de demande d’ouverture de connexion se produira presque immédiatement après les erreurs de connexion temporaires. Pour plus d’informations, consultez [Atténuation : Période de blocage du pool](~/docs/framework/migration-guide/mitigation-pool-blocking-period.md).|Mineur|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> <br /> <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>|Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, le protocole SSL 3 n’est plus celui utilisé par défaut quand il s’agit de négocier une connexion sécurisée.|Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 a toujours été inclus dans la liste de protocoles pour NetTcp. Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.<br /><br /> Si Ssl3 est exigé, vous pouvez utiliser un des mécanismes de configuration suivants pour ajouter Ssl3 à la liste des protocoles négociés :<br /><br /> -   La propriété <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName><br />- La propriété <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName><br />-   La section [\<transport>](~/docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md) de [\<netTcpBinding>](~/docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)<br />-   La section [\<sslStreamSecurity>](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) de [\<customBinding>](~/docs/framework/configure-apps/file-schema/wcf/custombinding.md)|Limité|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|La propriété `IsEnabled` du parent d’un contrôle <xref:System.Windows.Controls.TextBlock>|À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la modification de la propriété `IsEnabled` du parent d’un contrôle <xref:System.Windows.Controls.TextBlock> affecte tous les contrôles enfants (comme les liens hypertexte et boutons) du contrôle <xref:System.Windows.Controls.TextBlock>.<br /><br /> Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures de .NET Framework, les contrôles à l’intérieur d’un <xref:System.Windows.Controls.TextBlock> ne reflétaient pas toujours l’état de la propriété `IsEnabled` du parent du <xref:System.Windows.Controls.TextBlock>.|Cette modification est conforme au comportement attendu pour les contrôles à l’intérieur d’un contrôle <xref:System.Windows.Controls.TextBlock>.|Mineur|  
|Défilement horizontal, virtualisation et <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>|Le comportement de l’opération de défilement pour un <xref:System.Windows.Controls.ItemsControl> qui effectue sa propre virtualisation dans le sens orthogonal vers la direction de défilement principale a été modifié.|La modification génère une expérience plus prévisible et intuitive pour l’utilisateur final, mais il peut affecter n’importe quelle application qui dépend de la valeur exacte de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> après un défilement horizontal. Pour plus d’informations, consultez [Atténuation : Défilement horizontal et virtualisation](~/docs/framework/migration-guide/mitigation-horizontal-scrolling-and-virtualization.md).|Mineur|  
|Vérificateur orthographique WPF (classe <xref:System.Windows.Controls.SpellCheck?displayProperty=fullName>)|Trois problèmes signalés dans la vérification orthographique WPF lors de l’exécution sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ont été corrigées dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] :<br /><br /> -   Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], le vérificateur orthographique génère parfois une <xref:System.Runtime.InteropServices.COMException> lors de l’appel des méthodes [ISpellChecker](https://msdn.microsoft.com/library/windows/desktop/hh869767\(v=vs.85\).aspx) ou [ISpellCheckerFactory](https://msdn.microsoft.com/library/windows/desktop/hh869770\(v=vs.85\).aspx). Dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ces exceptions ont été éliminées.<br />-   [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], le vérificateur orthographique identifie incorrectement des fautes d’orthographe dans les mots composés, tels que « Hausnummer » en allemand. Dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], le vérificateur orthographique gère correctement les mots composés.<br />-   Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], le vérificateur orthographique lève une <xref:System.UnauthorizedAccessException> lorsqu’une application est lancée à l’aide de « Exécuter en tant qu'autre utilisateur ». Dans [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ce scénario n’est pas pris en charge et le vérificateur orthographique est désactivé en mode silencieux.|Ces modifications améliorent la robustesse du vérificateur orthographique.  Elles ne devraient pas affecter négativement une application, sauf si le code de l’application dépend du déclenchement d’une exception.|Limité|  
| Méthode [DataGridCellsPanel.BringIndexIntoView](xref:System.Windows.Controls.DataGridCellsPanel.BringIndexInfoView(System.Int32)) | Dans .NET Framework 4.6.2, la méthode **BringIndexIntoView** s’exécute de façon asynchrone lorsque la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas été déterminées. Cependant, si les colonnes sont supprimées avant la fin de l’opération asynchrone, une [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException) peut se produire.<br/></br>À compter du 4.7 de .NET Framework 4.7, l’exception n’est plus levée dans ce scénario. | Vous pouvez effectuer les opérations suivantes pour empêcher que cette exception se produise : <br/> - Mettez à niveau vers .NET Framework 4.7. <br/> 1 Installez le dernier correctif pour .NET Framework 4.6.2. <br/> - Évitez de supprimer des colonnes jusqu'à ce que la réponse asynchrone à la méthode [DataGrid.ScrollIntoView](xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)) soit terminée. | Limité | 
  
<a name="XML"></a>   
## <a name="signed-xml-verification-requirements"></a>Conditions requises pour la vérification XML signée  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> et <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName>|Le chargement de ressources externes est désactivé, et les id cibles ambigus sont considérés comme non valides.|Une exception est levée dans plusieurs cas, notamment les suivants :<br /><br /> -   Identification d’un élément par un attribut d’id et définition d’un deuxième élément avec le même identificateur,<br />-   Définition d’un identificateur qui n’est pas une valeur `NCName` autorisée.<br />-   Référencement d’URI externes.<br /><br /> <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A?displayProperty=fullName> retourne toujours `false` pour les documents :<br /><br /> -   Qui utilisent la transformation de référence XPath.<br />-   Qui utilisent la transformation de référence XSLT.<br /><br /> Les développeurs doivent vérifier l’utilisation de <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=fullName> et <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> ainsi que des types dérivés <xref:System.Security.Cryptography.Xml.Transform?displayProperty=fullName>, car un destinataire du document pourrait ne pas être en mesure de les traiter.<br /><br /> Pour plus d’informations, consultez [Après avoir appliqué la mise à jour de sécurité 3141780, les applications .NET Framework rencontrent des erreurs d’exception ou de défaillance inattendues lors du traitement de fichiers qui contiennent SignedXml](https://support.microsoft.com/en-us/kb/3148821).|Mineur|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications dans la version 4.6.2](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
