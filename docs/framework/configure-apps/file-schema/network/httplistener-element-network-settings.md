---
title: "&lt;httpListener&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; élément (paramètres réseau)
Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.  
  
 \<configuration>  
\<System.NET >  
\<Paramètres >  
\<httpListener >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Type  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|unescapeRequestUrl|Valeur booléenne qui indique si un <xref:System.Net.HttpListener> instance utilise l’URI sans séquence d’échappement brut au lieu de l’URI converti.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
 Le **unescapeRequestUrl** attribut indique si <xref:System.Net.HttpListener> utilise l’URI sans séquence d’échappement brut au lieu de l’URI converti où toutes les valeurs encodées de pourcentage sont converties et autres étapes de normalisation sont exécutées.  
  
 Lorsqu’un <xref:System.Net.HttpListener> instance reçoit une demande via le `http.sys` service, il crée une instance de la chaîne d’URI fournie par `http.sys`et l’expose en tant que le <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriété.  
  
 Le `http.sys` service expose deux chaînes d’URI de demande :  
  
-   URI brut  
  
-   URI converti  
  
 L’URI brut est le <xref:System.Uri?displayProperty=nameWithType> fourni dans la ligne de la demande d’une demande HTTP :  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 L’URI brut fourni par `http.sys` de la demande indiquée ci-dessus, est « chemin d’accès / ». Représente la chaîne qui suit le verbe HTTP, telle qu’elle a été envoyée sur le réseau.  
  
 Le `http.sys` service crée un URI converti à partir des informations fournies dans la demande à l’aide de l’URI fourni dans la ligne de la requête HTTP et l’en-tête d’hôte pour déterminer le serveur d’origine la demande doit être transféré à. Cela est effectué en comparant les informations de la requête avec un jeu de préfixes URI enregistrés. La documentation du SDK du serveur HTTP fait référence à cet URI converti en tant que structure HTTP_COOKED_URL.  
  
 Pour être en mesure de comparer la demande avec les préfixes URI enregistrés, une normalisation de la demande doit être effectué. Pour l’exemple ci-dessus, l’URI converti est comme suit :  
  
 `http://www.contoso.com/path/`  
  
 Le `http.sys` service associe le <xref:System.Uri.Host%2A?displayProperty=nameWithType> valeur de propriété et la chaîne dans la ligne de la requête pour créer un URI converti. En outre, `http.sys` et <xref:System.Uri?displayProperty=nameWithType> classe effectue également les opérations suivantes :  
  
-   N’échappe pas pourcentage de toutes les valeurs encodées.  
  
-   Caractères non ASCII encodés en pourcentage de convertit en une représentation de caractères UTF-16. Notez que les caractères UTF-8 et ANSI ou DBCS sont pris en charge, ainsi que des caractères Unicode (encodage Unicode à l’aide du format %uXXXX).  
  
-   Exécute les autres étapes de normalisation, comme la compression de chemin d’accès.  
  
 Étant donné que la demande ne contient pas d’informations sur l’encodage utilisé pour les valeurs encodées en pourcentage, il n’est peut-être pas possible de déterminer l’encodage correct seulement en analysant les valeurs encodées en pourcentage.  
  
 Par conséquent `http.sys` fournit deux clés de Registre pour la modification du processus :  
  
|Clé de Registre|Valeur par défaut|Description|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8 n'|1|Si zéro, `http.sys` accepte uniquement les URL encodée en UTF-8.<br /><br /> Si non nul, `http.sys` accepte également des URL ANSI ou DBCS dans les requêtes.|  
|FavorUTF8|1|Si non nul, `http.sys` toujours tente de décoder une URL au format UTF-8 ; si cette conversion échoue et EnableNonUTF8 n’est pas nulle, Http.sys, puis tente de décoder comme ANSI ou DBCS.<br /><br /> Si zéro (et EnableNonUTF8 n’est pas nulle), `http.sys` essaie de le décoder comme ANSI ou DBCS ; si cela ne réussit pas, il essaie une conversion UTF-8.|  
  
 Lorsque <xref:System.Net.HttpListener> reçoit une demande, il utilise l’URI converti de `http.sys` comme entrée pour le <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
 Il est nécessaire pour prendre en charge des caractères autres que des caractères et les nombres dans les URI. Un exemple est l’URI suivant, qui est utilisée pour récupérer des informations sur le client pour le client numéro « 1/3812 » :  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Notez la barre oblique d’encodés en pourcentage dans l’Uri (% 2F). Cela est nécessaire, car dans ce cas la barre oblique représente des données et pas un délimiteur de chemin d’accès.  
  
 Transmission de la chaîne au constructeur d’Uri entraîne l’URI suivant :  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Fractionner le chemin d’accès en segments entraînerait les éléments suivants :  
  
 `Customer('1`  
  
 `3812')`  
  
 Ce n’est pas l’intention de l’expéditeur de la demande.  
  
 Si le **unescapeRequestUrl** attribut a la valeur **false**, alors le <xref:System.Net.HttpListener> reçoit une demande, il utilise l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée pour le <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
 La valeur par défaut pour le **unescapeRequestUrl** attribut est **true**.  
  
 Le <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriété peut être utilisée pour obtenir la valeur actuelle de la **unescapeRequestUrl** attribut à partir des fichiers de configuration applicables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer le <xref:System.Net.HttpListener> lorsqu’il reçoit une demande pour utiliser l’URI brut au lieu de l’URI converti à partir de la classe `http.sys` comme entrée pour le <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
```xml  
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
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||
|-|-|  
|Espace de noms|System.Net|  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
