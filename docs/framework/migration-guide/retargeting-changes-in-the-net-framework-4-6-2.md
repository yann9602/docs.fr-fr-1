---
title: "Modifications du reciblage dans le .NET Framework 4.6.2 | Microsoft Docs"
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
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 76dc6849-8210-4e41-8731-20828c98b282
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229ccf3fa4ff1029334641da350cfd040e4b286e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-462"></a>Reciblage des modifications dans le .NET Framework 4.6.2
Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Elles n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous la version 4.6.2. Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] inclut des modifications de reciblage dans les domaines suivants :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
 La colonne Portée des tableaux suivants indique l'importance de chaque modification :  
  
-   Majeur. Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code. Notez qu'aucune des modifications de reciblage ne correspond à cette catégorie.  
  
-   Mineur. Modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
-   Limité. Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
-   Transparent. Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
<a name="Core"></a>   
## <a name="core"></a>Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Prise en charge des chemins d’accès longs|À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], les chemins d’accès longs (de jusqu’à 32 000 caractères) sont pris en charge et la limite de 260 caractères (ou `MAX_PATH`) sur la longueur du chemin d’accès est supprimée.|Pour les applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], les chemins de code qui levaient précédemment une <xref:System.IO.PathTooLongException> peuvent ne plus lever d’exception. Pour plus d’informations, consultez [Atténuation : Prise en charge des chemins d’accès longs](~/docs/framework/migration-guide/mitigation-long-path-support.md).|Mineur|  
|Normalisation des chemins d’accès|À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], le mode dans lequel les chemins d’accès sont normalisés a changé pour déférer l’opération au système d’exploitation et fournir un meilleur accès aux chemins de périphérique DOS.|Ces modifications permettent d’accéder à des chemins d’appareil valides qui n’étaient précédemment pas pris en charge. Pour plus d’informations, consultez [Atténuation : Normalisation des chemins d’accès](~/docs/framework/migration-guide/mitigation-path-normalization.md).|Mineur|  
|<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>|Plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et le format), à commencer par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.|Ces modifications bloquent certains chemins d’URI que ces deux méthodes prenaient précédemment en charge. Pour plus d’informations, consultez [Atténuation : Vérifications des signes deux-points dans les chemins d’accès](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|Limité|  
|Constructeur <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName>|À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> créée par un appel à la méthode <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> est une nouvelle instance de <xref:System.Security.Claims.ClaimsIdentity>. Dans les versions antérieures du .NET Framework, le <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> est une référence existante.|Dans certains cas, la comparaison de la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> avec la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> du <xref:System.Security.Principal.IIdentity> du constructeur retourne des résultats différents.<br /><br /> Pour plus d’informations, consultez [Atténuation : Constructeur ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|Limité|  
|<xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor%2A?displayProperty=fullName>|À partir des applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], le déchiffreur <xref:System.Security.Cryptography.AesCryptoServiceProvider> fournit une transformation réutilisable.   Après un appel à <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A>, la transformation est réinitialisée et peut être réutilisée.<br /><br /> Pour les applications qui ciblent des versions antérieures du .NET Framework, toute tentative de réutilisation du déchiffreur en appelant <xref:System.Security.Cryptography.ICryptoTransform.TransformBlock%2A> après un appel à <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> lève une <xref:System.Security.Cryptography.CryptographicException> ou génère des données endommagées.|L’impact devrait être minime, car il s’agit du comportement attendu.<br /><br /> Les applications qui dépendent du comportement précédent peuvent refuser la modification en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/> </runtime>`<br /><br /> En outre, les applications qui ciblent une version antérieure de .NET Framework mais s’exécutent sous une version .NET Framework ultérieure à [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] peuvent adopter cette modification en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/> </runtime>`|Mineur|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Prise en charge des certificats stockés à l’aide de CNG par la sécurité du transport WCF|La sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG), à commencer par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Cette prise en charge se limite aux certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette fonctionnalité est activée par défaut.<br /><br /> Dans les versions antérieures de .NET Framework, les tentatives d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent une exception.|Les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou des versions antérieures, mais qui s’exécutent sur [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] peuvent activer la prise en charge des certificats CNG en ajoutant la ligne suivante à la section runtime du fichier app.config ou web.config.<br /><br /> `<AppContextSwitchOverrides     value="Switch.System.ServiceModel.DisableCngCertificates=false" />`<br /><br /> Vous pouvez en faire autant par programmation avec un code de ce type :<br /><br /> `private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate"; AppContext.SetSwitch(disableCngCertificates, false);`<br /><br /> `Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates" AppContext.SetSwitch(disableCngCertificates, False)`<br /><br /> Notez qu’en raison de cette modification, tout code de traitement des exceptions qui dépend de l’échec de la tentative d’établissement d’une communication sécurisée avec un certificat CNG ne s’exécutera plus.|Mineur|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, `System.ComponentModel.EventDescriptor.Equals` et `System.ComponentModel.PropertyDescriptor.Equals`|À partir des applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], l’implémentation de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A> de classe de base a changé.|Étant donné que le test d’égalité produit maintenant le résultat attendu, cette modification devrait avoir peu d’effet.<br /><br /> Toutefois, les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] et dépendent du précédent comportement peuvent refuser cette modification. De même, les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sous [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] peuvent activer cette modification. Pour plus d’informations, consultez [Atténuation : MemberDescriptor.Equals](~/docs/framework/migration-guide/mitigation-memberdescriptor-equals.md).|Limité|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications dans la version 4.6.2](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
