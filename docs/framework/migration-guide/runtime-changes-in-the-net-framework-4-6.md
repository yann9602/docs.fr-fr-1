---
title: "Modifications du runtime dans le .NET Framework 4.6 | Microsoft Docs"
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
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6
- application compatibility
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 77002c3d1b6553156c225b3efba9a2f29009915a
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-46"></a>Modifications du runtime dans le .NET Framework 4.6
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. Il s'agit notamment des modifications dans les domaines suivants :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [Données](#Data)  
  
-   [Mise en réseau](#Networking)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [Configuration et déploiement](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Nouveau compilateur JIT 64 bits](#RyuJIT)  
  
<a name="Core"></a>   
## <a name="core"></a>Principal  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|À compter du [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la classe <xref:System.Globalization.PersianCalendar> utilise l’algorithme solaire hégirien.|L'algorithme solaire hégirien produit des résultats identiques à ceux du calendrier persan actuellement utilisé en Iran et Afghanistan. Il génère également des résultats identiques à l'algorithme précédent pour les dates entre 1800 et 2023 dans le calendrier grégorien. Les dates situées en dehors de cette plage peuvent être affectées si la classe <xref:System.Globalization.PersianCalendar> est utilisée pour effectuer des conversions de dates (par exemple, entre des dates du calendrier grégorien et des dates du calendrier persan) ou pour déterminer si une année donnée est une année bissextile.<br /><br /> En raison de ce changement, la valeur de la propriété <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> est passée de « 21 mars 0622 » à « 22 mars 0622 » pour les systèmes sur lesquels est installé le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].<br /><br /> Pour plus d’informations, consultez la rubrique relative à <xref:System.Globalization.PersianCalendar>.|Mineur|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|Pour le domaine d’application par défaut, la valeur de la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> est dérivée de <xref:System.Runtime.Versioning.TargetFrameworkAttribute> (s’il en existe un), sauf si elle est explicitement définie en assignant un nom à la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.  Dans les versions antérieures du .NET Framework, la valeur de l’attribut <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> est `null`, sauf si plusieurs chemins de code spéciaux sont exécutés ou un domaine d’application non défini par défaut est créé sans spécifier explicitement la version cible de .NET Framework dans la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.<br /><br /> Pour les domaines d’application non définis par défaut, la façon de déterminer la valeur de la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> reste la même. Si aucune valeur n’est explicitement affectée à la propriété <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>, le domaine d’application autre que celui par défaut hérite du nom de l’infrastructure cible du domaine d’application par défaut.|Pour le domaine d’application par défaut, <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> peut retourner une valeur non Null, alors qu’avant, il retournait `null`. Il s'agit du comportement souhaitable.|Limité|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|Si les certificats installés sur le système ne sont pas pris en charge par le .NET Framework, le passage d'une valeur `True` pour l'argument `verbose` retourne une chaîne valide. Dans les versions antérieures du .NET Framework, toute tentative d'accès aux informations de clé publique pour les certificats non pris en charge dans certaines situations entraîne la levée d'une exception.|Cette méthode est utilisée à titre d'information uniquement. La documentation indique qu'il est possible que la sortie ne soit pas cohérente selon les versions du .NET Framework. Ce changement affecte uniquement les applications qui appellent la méthode `ToString(True)`, et dont les certificats installés ne sont pas pris en charge par le .NET Framework. En retournant une chaîne au lieu de lever une exception, ce changement rend la méthode plus robuste.|Limité|  
|suivi d'événements pour Windows|Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et 4.6.1, le runtime lève une exception <xref:System.ArgumentException> lorsque deux noms d’événements diffèrent uniquement par le suffixe « Start » ou « Stop » (comme lorsqu’un événement est nommé `LogUser` et un autre `LogUserStart`). Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.|Vérifiez que vous n’avez pas deux noms d’événements qui diffèrent uniquement par le suffixe « Start » ou « Stop ».<br /><br /> À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette vérification n’est plus nécessaire. Le runtime est désormais capable de résoudre l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe « Start ».|Limité|  
|Réflexion et DCOM|Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus. Les types suivants sont affectés : <xref:System.Reflection.Assembly> ; <xref:System.Reflection.MemberInfo> et ses types dérivés, y compris <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Type> et <xref:System.Reflection.TypeInfo> ; <xref:System.Reflection.MethodBody> ; <xref:System.Reflection.Module> et <xref:System.Reflection.ParameterInfo>.|Les appels à [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) pour l’objet retournent `E_NOINTERFACE`.|Mineur|  
  
<a name="Data"></a>   
## <a name="data"></a>Données  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Une connexion TCP/IP à une base de données SQL Server qui se résout en `localhost`|À compter du [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la tentative de connexion échoue avec l’erreur « Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server. Le serveur est introuvable ou n’est pas accessible. Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions distantes. (Fournisseur : interface réseau SQL, Erreur : 26 - Erreur lors de la localisation du serveur/de l’instance spécifiés) »|Ce problème a été résolu et le comportement précédent a été restauré dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Pour vous connecter à une base de données SQL Server qui se résout en `localhost`, effectuez une mise à niveau vers le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)].|Mineur|  
  
<a name="Networking"></a>   
## <a name="networking"></a>Réseau  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Valeurs de date et heure dans la classe <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>.|Pour se conformer aux normes [RFC822](http://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](http://www.ietf.org/rfc/rfc2822.txt), les valeurs de date et heure comportent maintenant deux chiffres. Auparavant, un seul chiffre était utilisé pour les valeurs qui précédaient 10:00.|Ce changement affecte les scénarios d'usage suivants :<br /><br /> - Comparaison des longueurs ou des codes de hachage des objets <xref:System.Net.Mime.ContentDisposition> sérialisés dans les différentes versions du .NET Framework<br />- Comparaison de la valeur de retour de la méthode <xref:System.Net.Mime.ContentDisposition.ToString%2A> ou de la représentation sous forme de chaînes des valeurs de propriété de date et heure <xref:System.Net.Mime.ContentDisposition> dans les différentes versions du .NET Framework|Mineur|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Services WCF qui utilisent NETTCP avec la sécurité SSL et l’authentification par certificat|Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut. Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.|TLS 1.2 ne prend pas en charge l’authentification par certificat MD5. Par conséquent, si un client utilise un certificat MD5, le client WCF ne parviendra pas à se connecter au service WCF. Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).|Mineur|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Rendu de fenêtre dans un scénario à plusieurs écrans|La totalité de la fenêtre est restituée sans découpage lorsqu'elle s'étend au-delà d'un seul affichage dans un scénario à plusieurs écrans.|Consultez [Atténuation : Rendu de la fenêtre WPF](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md).|Mineur|  
|Vérificateur d'orthographe sur les contrôles WPF avec texte activé|Lors de l'exécution sur Windows 10, le vérificateur d'orthographe peut ne pas fonctionner, car les fonctionnalités de vérification orthographique de la plateforme ne sont disponibles que pour les langues présentes dans la liste des langues d'entrée.|Dans Windows, 10, lorsqu'une langue est ajoutée à la liste des claviers disponibles, Windows télécharge et installe automatiquement le package correspondant de fonctionnalités à la demande, qui fournit les fonctionnalités de vérification orthographique. En ajoutant la langue à la liste des langues d'entrée, le vérificateur d'orthographe est pris en charge.|Mineur|  
  
<a name="Setup"></a>   
## <a name="setup-and-deployment"></a>Configuration et déploiement  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Contrôle de version de produit|Le contrôle de version de produit a changé depuis les mises en production précédentes du .NET Framework, notamment pour le .NET Framework 4, 4.5, 4.5.1 et 4.5.2. Pour plus d’informations, consultez [Atténuation : contrôle de version de produit](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Consultez [Atténuation : contrôle de version de produit](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Moyenne|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Applications publiées avec ClickOnce, et qui utilisent un certificat de signature de code SHA-256.|Les applications ClickOnce qui ciblent [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou des versions antérieures, et qui sont signées avec un certificat SHA-256 n'ont plus de dépendance de runtime pour [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou une version ultérieure.|Avant, la signature d’une application ClickOnce qui ciblait le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou des versions antérieures avec un certificat SHA-256 nécessitait que le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou ultérieur soit présent sur le système cible. Cela générait des erreurs dans les cas où il n'était pas présent. Ce changement a supprimé cette dépendance et permet aux certificats SHA-256 d'être utilisés pour signer des applications ClickOnce qui ciblent [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] et les versions antérieures.|Mineur|  
  
<a name="RyuJIT"></a>   
## <a name="the-new-64-bit-jit-compiler"></a>Nouveau compilateur JIT 64 bits  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Compilation JIT 64 bits|À compter du .NET Framework 4.6, un nouveau compilateur JIT 64 bits est utilisé pour la compilation juste-à-temps. Ce changement n’affecte pas le compilateur JIT 32 bits.|Dans certains cas, une exception inattendue est levée ou un comportement d’application différent de celui lié à l’utilisation d’un compilateur 32 bits ou d’un compilateur JIT 64 bits est observé. **Remarque** : Tous ces problèmes ont été résolus dans le nouveau compilateur 64 bits fourni avec le SDK .NET Framework 4.6.2. La plupart ont également été résolus dans les versions de maintenance du .NET Framework 4.6 et 4.6.1, qui sont disponibles via Windows Update. <br /><br /> Pour plus d’informations, consultez [Atténuation : Nouveau compilateur JIT 64 bits](../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md).|Limité|  
|Gestion des exceptions (retour à partir d'une région `try`)|À la différence du compilateur juste-à-temps JIT 64 bits, le nouveau compilateur JIT 64 bits n’autorise pas les instructions `ret` de code IL dans une région `try`.|Le retour à partir d'une région `try` n'est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL. Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.<br /><br /> Si votre application génère du langage intermédiaire comprenant un opcode `ret` dans une région `try`, vous pouvez :<br /><br /> - Cibler le .NET Framework 4.5 ou ajouter l’élément [\<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) au fichier de configuration de votre application pour utiliser l’ancien compilateur JIT et contourner le changement<br />- Mettez à jour le langage intermédiaire généré à retourner après la région `try`<br />-|Limité|
