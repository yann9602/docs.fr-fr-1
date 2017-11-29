---
title: "&lt;Supprimez&gt; , élément de schemeSettings (paramètres d’Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6d587dced4660774b67a8e884bf6c25df3b6e400
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a>&lt;Supprimez&gt; , élément de schemeSettings (paramètres d’Uri)
Supprime un paramètre de schéma pour un nom de schéma.  
  
 \<configuration>  
\<URI >  
\<schemeSettings >  
\<Supprimer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Le nom du schéma auquel ce paramètre s’applique. Les seules valeurs prises en charge sont nom = « http » et le nom = « https ».|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<schemeSettings, élément (paramètres d’Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, le <xref:System.Uri?displayProperty=nameWithType> pour cent de classe n’échappe pas encodée séparateurs de chemin d’accès avant d’exécuter la compression de chemin d’accès. Cela a été implémenté en tant que mécanisme de sécurité contre les attaques comme suit :  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Si cet URI est passé à des modules ne gère ne pas % correctement les caractères encodés, elle peut entraîner la commande suivante, exécutée par le serveur :  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Pour cette raison, <xref:System.Uri?displayProperty=nameWithType> première séparateurs de chemin d’accès n’échappe pas de classe, puis applique la compression de chemin d’accès. Le résultat du passage de l’URL malveillante ci-dessus pour <xref:System.Uri?displayProperty=nameWithType> classe constructeur se traduit par l’URI suivant :  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Ce comportement par défaut peut être modifié pour ne pas les délimiteurs de chemin d’accès codé en pourcentage échapper à l’aide de l’option de configuration schemeSettings pour un modèle spécifique.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une configuration utilisée par la <xref:System.Uri> classe qui supprime les paramètres de schéma pour le schéma http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
