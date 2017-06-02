---
title: "Pr&#233;sentation des probl&#232;mes et exceptions de WebRequest | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Pr&#233;sentation des probl&#232;mes et exceptions de WebRequest
<xref:System.Net.WebRequest> et ses classes dérivées \(<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, et <xref:System.Net.FileWebRequest>\) lèvent des exceptions pour signaler une différence.  Parfois la résolution de ces problèmes n'est pas évident.  
  
## Solutions  
 Examinez la propriété d' <xref:System.Net.WebException.Status%2A> d' <xref:System.Net.WebException> pour déterminer le problème.  Le tableau suivant montre plusieurs valeurs d'état et des résolutions possibles.  
  
|État|Détails|Solution|  
|----------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus><br /><br /> ou<br /><br /> <xref:System.Net.WebExceptionStatus>|Un problème avec le socket sous\-jacent.  La connexion a peut\-être été réinitialisation.|Reconnectez et retournez la demande.<br /><br /> Assurez\-vous que le dernier Service Pack est installé.<br /><br /> Augmentez la valeur de la propriété d' <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=fullName> .<br /><br /> Affectez à <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=fullName> la valeur `false`.<br /><br /> Augmentez le nombre maximal de connexions à la propriété d' <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Vérifiez la configuration de proxy.<br /><br /> Si vous utilisez SSL, assurez \-vous que le processus serveur a l'autorisation d'accéder au magasin de certificats.<br /><br /> Si l'envoi de grandes quantités de données, définissez <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> à `false`.|  
|<xref:System.Net.WebExceptionStatus>|Le certificat de serveur n'a pas pu être validée.|Essayez d'ouvrir l'URI à l'aide de Internet Explorer.  Résolvez toutes les alertes sécurité affichées par l'IE.  Si vous ne pouvez pas résoudre l'alerte sécurité, vous pouvez créer une classe de stratégie de certificat qui implémente <xref:System.Net.ICertificatePolicy> qui retourne `true`, et le passe à <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.<br /><br /> Consultez [http:\/\/support.microsoft.com\/?id\=823177](http://go.microsoft.com/fwlink/?LinkID=179653).<br /><br /> Assurez \-vous que le certificat de l'autorité de certification qui a archivé le certificat de serveur est ajouté à la liste approuvée d'autorité de certification dans Internet Explorer.<br /><br /> Assurez \-vous que le nom d'hôte dans l'URL correspond au nom commun sur le certificat de serveur.|  
|<xref:System.Net.WebExceptionStatus>|Une erreur s'est produite dans la transaction SSL, ou un problème de certificat.|La version 3,0 de SSL de charge par le .NET Framework version 1.1 uniquement.  Si le serveur utilise uniquement la version 1,0 TLS ou la version 2,0 de SSL, l'exception est levée.  Mise à jour du .NET Framework version 2.0, et définir <xref:System.Net.ServicePointManager.SecurityProtocol%2A> pour correspondre au serveur.<br /><br /> Le certificat client a été signé par une autorité de certification \(CA\) à laquelle le serveur n'est pas approuvée.  Installez le certificat de l'autorité de certification sur le serveur.  Consultez [http:\/\/support.microsoft.com\/?id\=332077](http://go.microsoft.com/fwlink/?LinkID=179654).<br /><br /> Assurez \-vous que l'installation du dernier Service Pack.|  
|<xref:System.Net.WebExceptionStatus>|Échec de la connexion.|Un pare\-feu ou un proxy bloque la connexion.  Modifiez le pare\-feu ou proxy pour permettre la connexion.<br /><br /> Indiquez explicitement <xref:System.Net.WebProxy> dans l'application cliente en appelant le constructeur d' <xref:System.Net.WebProxy> \(WebServiceProxyClass.Proxy \= nouveaux WebProxy \([http:\/\/server:80](http://server/)true\),\).<br /><br /> Exécutez Filemon ou Regmon pour vérifier que l'identité du processus de travail a des autorisations requises pour accéder à WSPWSP.dll, HKLM \\System\\CurrentControlSet\\Services\\DnsCache or HKLM\\System\\CurrentControlSet\\Services\\WinSock 2.|  
|<xref:System.Net.WebExceptionStatus>|Nomdomaine le service ne peut pas résoudre le nom d'hôte.|Configurez proxy correctement.  Consultez [http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Assurez \-vous qu'aucun logiciel antivirus ou de pare\-feu installé ne bloque la connexion.|  
|<xref:System.Net.WebExceptionStatus>|<xref:System.Net.WebRequest.Abort%2A> a été appelé, ou une erreur s'est produite.|Ce problème peut être provoquée par une charge importante sur le client ou le serveur.  Réduire la charge.<br /><br /> Augmentez la définition d' <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Consultez [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) la modification des paramètres de performances de service Web.|  
|<xref:System.Net.WebExceptionStatus>|L'application a tenté de l'écriture à un socket qui a déjà été fermé.|Le client ou le serveur est surchargé.  Réduire la charge.<br /><br /> Augmentez la définition d' <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> .<br /><br /> Consultez [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) la modification des paramètres de performances de service Web.|  
|<xref:System.Net.WebExceptionStatus>|Le jeu de limite \(<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>\) sur la longueur de message a été dépassé.|Augmentez la valeur de la propriété d' <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> .|  
|<xref:System.Net.WebExceptionStatus>|Nomdomaine le service ne peut pas résoudre le nom d'hôte de proxy.|Configurez proxy correctement.  Consultez [http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Pour forcer <xref:System.Net.HttpWebRequest> n'utiliser un proxy en affectant à la propriété d' <xref:System.Net.HttpWebRequest.Proxy%2A> à `null`.|  
|<xref:System.Net.WebExceptionStatus>|La réponse du serveur n'est pas une réponse HTTP valide.  Ce problème se produit lorsque le.NET Framework détecte que la réponse de serveur n'est pas conforme à la norme RFC HTTP 1,1.  Ce problème se produit lorsque la réponse contient les en\-têtes non valides ou l'en\-tête non valide delimiters.RFC 2616 définit HTTP 1,1 et le format valide pour la réponse du serveur.  Pour plus d'informations, consultez [http:\/\/www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388).|Obtenez une trace réseau de la transaction et examinez les en\-têtes dans la réponse.<br /><br /> Si votre application requiert la réponse de serveur sans analyser \(il peut s'agir d'un problème de sécurité\), définissez `useUnsafeHeaderParsing` à `true` dans le fichier de configuration.  Consultez [\<httpWebRequest\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## Voir aussi  
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.Dns>