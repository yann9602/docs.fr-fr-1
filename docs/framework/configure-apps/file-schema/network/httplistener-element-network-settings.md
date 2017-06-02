---
title: "&lt;httpListener&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;httpListener&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Personnalise les paramètres utilisés par la classe <xref:System.Net.HttpListener>.  
  
## Syntaxe  
  
```  
  
      <httpListener  
  unescapeRequestUrl ="true|false"  
/>  
```  
  
## Type  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|unescapeRequestUrl|Valeur booléenne qui indique si une instance <xref:System.Net.HttpListener> utilise l'URI brut sans séquence d'échappement plutôt que l'URI converti.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
 L'attribut **unescapeRequestUrl** indique si <xref:System.Net.HttpListener> utilise l'URI brut sans séquence d'échappement plutôt que l'URI converti où toutes les valeurs encodées de pourcentage sont converties et d'autres étapes de normalisation sont exécutées.  
  
 Lorsqu'une instance <xref:System.Net.HttpListener> reçoit une requête via le service `http.sys`, elle crée une instance de la chaîne d'URI fournie par `http.sys` et l'expose comme propriété <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=fullName>.  
  
 Le service `http.sys` expose deux chaînes d'URI de requête :  
  
-   URI brut  
  
-   URI converti  
  
 L'URI brut est le <xref:System.Uri?displayProperty=fullName> fourni dans la ligne de requête d'une requête HTTP :  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 L'URI brut fourni par `http.sys` pour la requête indiquée plus haut est « \/path\/ ».  Cela représente la chaîne qui suit le verbe d'HTTP envoyé sur le réseau.  
  
 Le service `http.sys` crée un URI converti à partir des informations fournies dans la demande à l'aide de l'URI fourni dans la ligne de requête HTTP et de l'en\-tête de l'hôte pour déterminer le serveur d'origine auquel la demande doit être transférée.  Cela est fait en comparant les informations de la requête avec un jeu de préfixes URI enregistrés.  La documentation du Kit de développement logiciel du serveur HTTP fait référence à cet URI converti en tant que structure HTTP\_COOKED\_URL.  
  
 Pour être en mesure de comparer la demande avec les préfixes URI enregistrés, une normalisation de la demande doit être effectuée.  Pour l'exemple ci\-dessus, l'URI converti serait comme suit :  
  
 `http://www.contoso.com/path/`  
  
 Le service `http.sys` combine la valeur de propriété <xref:System.Uri.Host%2A?displayProperty=fullName> et la chaîne dans la ligne de demande pour créer un URI converti.  De plus, `http.sys` et la classe <xref:System.Uri?displayProperty=fullName> effectue également les opérations suivantes :  
  
-   Place hors d'une séquence d'échappement toutes les valeurs de pourcentage encodées.  
  
-   Convertit des caractères non ASCII encodés de pourcentage en une représentation de caractères UTF\-16.  Notez que les caractères UTF\-8 et ANSI\/DBCS sont pris en charge, de même que les caractères Unicode \(encodage Unicode à l'aide du format %uXXXX\).  
  
-   Exécute d'autres étapes de normalisation, comme la compression de chemin d'accès.  
  
 Puisque la demande ne contient pas d'informations sur l'encodage utilisé pour des valeurs encodées en pourcentage, il peut ne pas être possible de déterminer l'encodage correct seulement en analysant les valeurs encodées en pourcentage.  
  
 Par conséquent, `http.sys` fournit deux clés de Registre pour la modification du processus :  
  
|Clé de Registre|Valeur par défaut|Description|  
|---------------------|-----------------------|-----------------|  
|EnableNonUTF8|1|Si la valeur est zéro, `http.sys` accepte uniquement les URL encodées en UTF\-8.<br /><br /> Si non nul, `http.sys` accepte également des URL ANSI ou DBCS dans les requêtes.|  
|FavorUTF8|1|Si non nul, `http.sys` essaie toujours de décoder en premier une URL comme UTF\-8 ; si cette conversion échoue et EnableNonUTF8 n'est pas nul, Http.sys essaie de le décoder comme ANSI ou DBCS.<br /><br /> Si la valeur est zéro \(et si EnableNonUTF8 est différent de zéro\), `http.sys` essaie de le décoder en ANSI ou DBCS ; si cela échoue, il essaie une conversion en UTF\-8.|  
  
 Lorsque <xref:System.Net.HttpListener> reçoit une requête, il utilise l'URI converti à partir de `http.sys` comme entrée pour la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 La prise en charge de caractères est nécessaire, outre les caractères et les nombres dans les URI.  L'URI suivant est un exemple d'URI utilisé pour extraire le numéro de client « 1\/3812 » :  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Notez la barre oblique encodée de pourcentage dans l'Uri \(%2F\).  Cela est nécessaire, puisque dans ce cas la barre oblique représente des données et non un délimiteur de chemin d'accès.  
  
 Le passage de la chaîne au constructeur d'Uri mènera à l'URI suivant :  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Le fractionnement du chemin d'accès en segments donne les éléments suivants :  
  
 `Customer('1`  
  
 `3812')`  
  
 Ce n'est pas l'intention de l'émetteur de la requête.  
  
 Si l'attribut **unescapeRequestUrl** est défini à **false**,  lorsque le <xref:System.Net.HttpListener> reçoit une demande, il utilise l'URI brut au lieu de l'URI converti de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 La valeur par défaut de l'attribut **unescapeRequestUrl** est **true**.  
  
 La propriété <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> peut être utilisée pour obtenir la valeur actuelle de l'attribut **unescapeRequestUrl** de fichiers de configuration applicables.  
  
## Exemple  
 L'exemple de code suivant montre comment configurer la classe <xref:System.Net.HttpListener> lorsqu'elle reçoit une requête visant à utiliser l'URI brut au lieu de l'URI converti à partir de `http.sys` en tant qu'entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms|System.Net|  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## Voir aussi  
 <xref:System.Net.Configuration.HttpListenerElement>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerRequest.Url%2A>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)