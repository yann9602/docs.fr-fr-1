---
title: "D&#233;tection automatique de proxy | Microsoft Docs"
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
helpviewer_keywords: 
  - "détections automatiques de proxy"
  - "Découverte automatique de proxy web"
  - "proxy web"
  - "détection automatique de serveurs proxy"
  - "WebProxy (classe), détections automatiques de proxy"
  - "serveurs proxy, détecter automatiquement"
  - "réseau"
  - "WPAD (découverte automatique de proxy web)"
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# D&#233;tection automatique de proxy
La détection automatique de proxy est un processus par lequel un serveur proxy Web est identifié par le système et utilisé pour envoyer des demandes de la part de le client.  Cette fonctionnalité est également connue sous le nom de WPAD \(Web Proxy Auto\-Discovery\).  Si la détection automatique de proxy est activée, le système tente de localiser un script de configuration de proxy qui est chargée de retourner l'ensemble de proxy qui peuvent être utilisés pour la demande.  Si le script de configuration de proxy est trouvé, le script est téléchargé, compilé, et exécuté sur l'ordinateur local lorsque les informations de proxy, le flux de demande, ou la réponse sont obtenus pour une requête qui utilise une instance d' <xref:System.Net.WebProxy> .  
  
 La détection automatique de proxy est effectuée par la classe d' <xref:System.Net.WebProxy> et peut utiliser des paramètres de demande niveau, les paramètres des fichiers de configuration, les paramètres spécifiés à l'aide de la boîte de dialogue d'Internet Explorer **Réseau local** .  
  
> [!NOTE]
>  Vous pouvez afficher la boîte de dialogue d'Internet Explorer **Paramètres du réseau local** en sélectionnant **Outils** du menu principal d'Internet Explorer et en sélectionnant **Options Internet**.  Ensuite, sélectionnez l'onglet **Connexions** , puis cliquez sur **Paramètres réseau**.  
  
 Si la détection automatique de proxy est activée, les tentatives de classe d' <xref:System.Net.WebProxy> de trouver le script de configuration de proxy comme suit :  
  
1.  La fonction WinINet `InternetQueryOption` est utilisée pour accéder au script de configuration de proxy récemment détecté par Internet Explorer.  
  
2.  Si le script n'est pas localisé, la classe d' <xref:System.Net.WebProxy> utilise le protocole DHCP \(DHCP\) pour accéder au script.  Le serveur DHCP peut répondre à l'emplacement \(nom d'hôte\) du script ou avec l'URL complète pour le script.  
  
3.  Si le DHCP ne reconnaît pas l'hôte de WPAD, le DNS est interrogé pour un hôte avec WPAD comme son nom ou l'alias.  
  
4.  Si l'hôte n'est pas reconnu et l'emplacement d'un script de configuration de proxy est spécifié par les paramètres du RÉSEAU LOCAL d'Internet Explorer ou un fichier de configuration, cet emplacement est utilisé.  
  
> [!NOTE]
>  Les applications qui s'exécutent comme NT entretiennent ou partie d'ASP.NET utilisent les paramètres du serveur proxy d'Internet Explorer \(si disponible\) de l'utilisateur appelant.  Ces paramètres peuvent ne pas être disponibles pour toutes les applications de service.  
  
 Les proxies sont configurés sur un par \- connectoid base.  Un connectoid est un élément dans la boîte de dialogue de connexion réseau, et peut être un périphérique réseau physique \(un modem ou une carte Ethernet\) ou une interface virtuelle \(telle qu'une connexion VPN exécutant sur un périphérique réseau\).  Lorsqu'un connectoid change \(par exemple, une connexion sans fil modifie un point d'accès, ou un VPN est activée\), l'algorithme de détection de proxy est exécuté à nouveau.  
  
 Par défaut, les paramètres de proxy d'Internet Explorer sont utilisés pour détecter le proxy.  Si votre application s'exécute sous un compte non interactif \(sans moyen pratique de configurer des paramètres de proxy d'IE\), ou si vous souhaitez utiliser des paramètres du proxy différent des paramètres IE de, vous pouvez configurer votre proxy en créant un fichier de configuration avec les éléments de [\<defaultProxy\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) et de [\<proxy\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) définis.  
  
 Pour les applications que vous créez, vous pouvez désactiver la détection automatique de proxy sur la requête de niveau à l'aide de <xref:System.Net.WebRequest.Proxy%2A> null avec votre application, comme indiqué dans l'exemple de code suivant.  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 Requêtes qui n'ont pas le proxy par défaut domaine d'application de proxy l'utilisation d'un votre, disponible dans la propriété d' <xref:System.Net.WebRequest.DefaultWebProxy%2A> .  
  
## Voir aussi  
 <xref:System.Net.WebProxy>   
 <xref:System.Net.WebRequest>   
 [\<system.Net\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)