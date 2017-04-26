---
title: "Modifications du reciblage dans le .NET Framework 4.7 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes,.NET Framework
- retargeting changes,.NET Framework 4.7
- application compatibility
ms.assetid: d98bf1e3-0017-4933-8e7b-191ac3542fcc
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2881049ee490bf0abdd8b2f0651ca3703ccae76a
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-47"></a>Reciblage des modifications dans le .NET Framework 4.7

Dans de rares cas, les modifications de reciblage peuvent affecter les applications recompilées pour cibler le .NET Framework 4.7. Elles n'affectent pas les fichiers binaires qui ciblent une version antérieure du .NET Framework mais s'exécutent sous la version 4.7. Le .NET Framework 4.7 apporte des modifications de reciblage dans les domaines suivants :  

-   [Fonctionnalités de base](#Core)  
-   [ASP.NET](#asp) 
-   [Windows Communication Foundation (WCF)](#WCF)  
-   [Windows Presentation Foundation (WPF)](#WPF)
 
 La colonne Portée des tableaux suivants indique l'importance de chaque modification :  
  
-   Majeur. Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code. Notez qu'aucune des modifications de reciblage ne correspond à cette catégorie.  
  
-   Mineur. Modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
-   Limité. Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
-   Transparent. Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
## <a name="a-namecore--core"></a><a name="Core" /> Core

| Fonctionnalité | Modification | Impact | Portée |
|----|----|----|----|
|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> | Les applications qui ciblent .NET Framework 4.6.2 et versions antérieures s’attendent à ce que la valeur affectée à cette propriété soit un <xref:System.IntPtr> vers l’emplacement spécifié dans la mémoire où réside la valeur HWND.<br/></br>Dans les applications qui ciblent .NET Framework 4.7, une application Windows Forms peut définir la valeur de cette propriété avec du code, comme suit : <br/><br/>` cspParameters.ParentWindowHandle = form.Handle; ` | Les applications qui trouvent ce changement de comportement gênant peuvent le désactiver. De même, les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sous .NET Framework 4.7 peuvent activer ce nouveau comportement. Pour plus d’informations, consultez [Atténuation : CspParameters.ParentWindowHandle attend un HWND](../../../docs/framework/migration-guide/mitigation-cspparameters-parentwindowhandle-expects-an-hwnd.md). | Mineur |
| Sérialisation avec la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> | À compter des applications qui ciblent .NET Framework 4.7, la sérialisation des caractères de contrôle avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>est est désormais compatible avec ECMAScript V6 et V8 | Cette modification est conforme à la norme ECMAScript et devrait avoir un impact limité. Si c’est le cas, un commutateur de compatibilité est disponible pour restaurer le comportement précédent. Pour plus d’informations, consultez [Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer | Microsoft Docs](../../../docs/framework/migration-guide/mitigation-serialization-control-characters.md)  | Limité |

## <a name="a-nameasp--aspnet"></a><a name="asp" /> ASP.NET

| Fonctionnalité  |Modification  |Impact | Portée | 
---------|---------|---------|-----|
Restriction des demandes simultanées par session | Dans .NET Framework 4.6.2 et versions antérieures, ASP.NET exécute les requêtes avec le même <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> séquentiellement, et ASP.NET émet toujours <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> via un cookie par défaut. Si une page prend beaucoup de temps à se charger, appuyer sur <kbd>F5</kbd> dans le navigateur dégrade considérablement les performances du serveur.<br/><br/>À compter de .NET Framework 4.7, un compteur effectue le suivi des demandes en file d’attente et arrête les demandes lorsqu’elles dépassent une limite spécifiée. La valeur par défaut est 50. Si la limite est atteinte, un avertissement est consigné dans le journal des événements et une réponse HTTP 500 peut être enregistrée dans le journal d’IIS.|Cette modification peut améliorer les performances globales du serveur.<br/><br/>Pour restaurer l’ancien comportement, vous pouvez ajouter le paramètre suivant à votre fichier web.config pour désactiver le nouveau comportement.<br/><br/>`<appSettings>`<br/>&nbsp;&nbsp;&nbsp;`<add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>`<br/>`</appSettings>` | Limité |

## <a name="a-namewcf--windows-communication-foundation"></a><a name="WCF" /> Windows Communication Foundation

| Fonctionnalité  |Modification  |Impact | Portée | 
---------|---------|---------|-----|
| Sécurité des messages (WCF) | Les applications qui s’exécutent sous le .NET Framework 4.7 ou versions ultérieures sont en mesure d’utiliser TLS 1.1 et TLS 1.2 pour la sécurité des messages (WCF) via les paramètres de configuration d’application. Il s’agit d’une fonctionnalité à activer ; par défaut, la prise en charge de TLS 1.1 et TLS 1.2 pour la sécurité des messages (WCF) est désactivée. | Le comportement par défaut pour la sécurité des messages (WCF) reste inchangé. <br/><br/> Pour activer la prise en charge de TLS 1.1 et TLS 1.2, ajoutez le paramètre de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier `app.config` ou `web.config` :  <br/><br/>`<runtime>` <br/> &nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;`<br/>&nbsp;&nbsp;&nbsp;`Switch.System.Net.DontEnableSchUseStrongCrypto=false" />`<br/>`</runtime>` | Limité |         

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)  

| Fonctionnalité | Modification | Impact | Portée |
|---|---|---|---|
| L’allocation d’espace de contrôle <xref:System.Windows.Controls.Grid> à des colonnes en étoile | À compter des applications qui ciblent .NET Framework 4.7, WPF remplace l’algorithme que le contrôle <xref:System.Windows.Controls.Grid> utilise pour allouer de l’espace aux \*-columns.md.) | Pour les applications qui ciblent les versions ultérieures à .NET Framework 4.7, cette modification affecte la largeur réelle affectée aux colonnes \* dans différents cas. Si cette modification n’est pas souhaitable, l’algorithme précédent peut continuer à s’appliquer en ajoutant une entrée au fichier de configuration de l’application. Pour plus d’informations, consultez [Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile](../../../docs/framework/migration-guide/mitigation-grid-control.md). | Mineur |
| <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> | Dans les applications qui ciblent .NET Framework 4.6.2 et versions antérieures, une erreur dans le code de gestion des exceptions pour la méthode <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A>provoquait une exception [NullReferenceException] (assetId:///T:System.NullReferenceException] au lieu de l’exception prévue (comme [DirectoryNotFoundException](assetId:///T:System.IO.DirectoryNotFoundException) ou [FileNotFoundException](assetId:///T:System.IO.FileNotFoundException).<br/><br/>Depuis les applications qui ciblent .NET Framework 4.7, la bonne exception levée.  | Les applications qui ciblent .NET Framework 4.7 et dépendent de la gestion d’une [NullReferenceException](assetId:///T:System.NullReferenceException) peuvent restaurer le comportement précédent en ajoutant ce qui suit aux paramètres de configuration de la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) dans le fichier `app.config` : <br/><br/>`<runtime>`<br/>&nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true"/>`<br/>`</runtime>`| Limité | 
| Prise en charge à activer pour une pile tactile/de stylet basée sur `WM_POINTER` | À compte des applications qui ciblent .NET Framework 4.7, WPF prend en charge une option tactile basée sur WM_POINTER.  | Il s’agit d’une fonctionnalité à activer qui est disponible sur les systèmes Windows à compter de Windows 10 Creators Update. Les applications WPF qui n’acceptent pas explicitement la prise en charge tactile/des stylets basée sur le pointeur ne sont pas affectées. Pour plus d’informations, consultez [Atténuation : Prise en charge du pointeur tactile et du stylet](../Topic/Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md). | Limité |
| Classe [PrintQueue](assetId:///T:System.Printing.PrintQueue) | À compter de .NET Framework 4.7, les API d’impression WPF qui utilisent [PrintQueue](assetId:///T:System.Printing.PrintQueue) appellent par défaut l’API Windows Print Document Package au lieu de l’API d’impression XPS désormais obsolète.<br/><br/>L’ancienne pile d’impression continue à fonctionner comme auparavant sur les versions antérieures de Windows. | Ni les utilisateurs ni les développeurs ne devraient voir de changements de comportement ou d’utilisation de l’API. <br/><br/>Pour utiliser l’ancienne pile dans Windows 10 Creators Update, définissez la valeur `UseXpsOMPrinting` `REG_DWORD` de la clé de registre `HKEY_CURRENT_USER\Software\Microsoft.NETFramework\Windows Presentation Foundation\Printing` sur 1. | Limité | 
## <a name="see-also"></a>Voir aussi
[Compatibilité d'applications dans le .NET Framework 4.7](Application%20Compatibility%20in%20the%20.NET%20Framework%204.7.md)

