---
title: "Gestion des connexions | Microsoft Docs"
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
  - "Internet, connexions"
  - "HTTP, classes pour la connexion"
  - "requête de données sur Internet, connexions"
  - "envoi de données, connexions"
  - "réception de données, connexions"
  - "ServicePoint (classe), à propos de la classe ServicePoint"
  - "réponse à une requête Internet, connexions"
  - "connexions (.NET Framework), classes"
  - "ressources réseau, connexions"
  - "téléchargement de ressources Internet, connexions"
  - "ServicePointManager (classe), à propos de la classe ServicePointManager"
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Gestion des connexions
Les applications qui utilisent HTTP pour se connecter aux ressources de données peuvent utiliser les classes d' <xref:System.Net.ServicePoint> et d' <xref:System.Net.ServicePointManager> du.NET framework pour gérer des connexions à Internet et pour les aider à accomplir l'échelle et optimiser les performances.  
  
 La classe de **ServicePoint** propose une application un point de terminaison auquel l'application à se connecter aux ressources Internet en accès.  Chaque **ServicePoint** contient des informations qui permet d'optimiser les connexions à un serveur Web en partageant les informations d'optimisation entre les plug\-ins pour améliorer les performances.  
  
 Chaque **ServicePoint** est identifié par un URI \(URI\) et est catégorisée en fonction de les fragments d'identificateur et d'hôte de modèle de l'URI.  Par exemple, la même instance de **ServicePoint** fournirait des requêtes aux URI http:\/\/www.contoso.com\/index.htm et http:\/\/www.contoso.com\/news.htm?date\=today parce qu'elles ont le même identificateur de modèle \(HTTP\) et les fragments hôte \(www.contoso.com\).  Si l'application a déjà une connexion persistante au serveur www.contoso.com, il utilise cette connexion pour récupérer les deux applications, évitant de créer deux connexions.  
  
 **ServicePointManager** est une classe statique qui gère la création et la destruction des instances de **ServicePoint** .  **ServicePointManager** crée **ServicePoint** lorsque l'application demande une ressource Internet qui n'est pas dans la collection d'exister des instances de **ServicePoint** .  Les instances de**ServicePoint** sont perdues lorsqu'il a dépassé sa durée d'inactivité maximum ou lorsque le nombre d'exister des instances de **ServicePoint** dépasse le nombre maximal d'instances de **ServicePoint** pour l'application.  Vous pouvez contrôler la durée d'inactivité maximum par défaut et le nombre maximal d'instances de **ServicePoint** en définissant les propriétés d' <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> et d' <xref:System.Net.ServicePointManager.MaxServicePoints%2A> sur **ServicePointManager**.  
  
 Le nombre de connexions entre un client et serveur peut avoir un impact excessive sur le débit d'application.  Par défaut, une application à l'aide de la classe d' <xref:System.Net.HttpWebRequest> utilise un maximum de deux connexions persistantes à un serveur donné, mais vous pouvez définir le nombre maximal de connexions pour chaque application.  
  
> [!NOTE]
>  Les limites de la spécification HTTP\/1.1 le nombre de connexions d'une application à deux connexions par serveur.  
  
 Le nombre optimal de connexions dépend des conditions réelles dans lesquelles l'application s'exécute.  Augmenter le nombre de connexions disponibles pour l'application peut ne pas affecter les performances de l'application.  Pour déterminer l'impact de plus de connexions, les tests de performance exécutés en faisant varier le nombre de connexions.  Vous pouvez modifier le nombre de connexions qu'une application utilise en modifiant la propriété statique d' <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> sur la classe de **ServicePointManager** à l'initialisation de l'application, comme indiqué dans l'exemple de code suivant.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Modifier la propriété de **ServicePointManager.DefaultConnectionLimit** n'affecte pas les instances précédemment initialisées de **ServicePoint** .  Le code suivant montre comment modifier la limite de connexion sur **ServicePoint** existant pour le serveur http:\/\/www.contoso.com à la valeur stockée dans `newLimit`.  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## Voir aussi  
 [Regroupement de connexions](../../../docs/framework/network-programming/connection-grouping.md)   
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)