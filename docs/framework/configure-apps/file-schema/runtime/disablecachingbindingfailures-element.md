---
title: "&lt;disableCachingBindingFailures&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableCachingBindingFailures> (élément)"
  - "assemblys (.NET Framework), mettre en cache les échecs de liaison"
  - "mettre en cache les échecs de liaison d'assemblys"
  - "disableCachingBindingFailures (élément)"
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;disableCachingBindingFailures&gt;, &#233;l&#233;ment
Spécifie s'il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l'assembly n'a pas été détecté.  
  
## Syntaxe  
  
```  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie s'il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l'assembly n'a pas été détecté.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|0|Ne désactivez pas la mise en cache des échecs de liaison qui se produisent parce que l'assembly était introuvable par détection.  Il s'agit du comportement de liaison par défaut introduit avec .NET Framework version 2.0.|  
|1|Désactivez la mise en cache des échecs de liaison qui se produisent parce que l'assembly était introuvable par détection.  Ce paramètre rétablit le comportement de liaison du .NET Framework version 1.1.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Si vous démarrez le .NET Framework version 2.0, le comportement par défaut du chargement d'assemblys est de mettre en cache toutes les défaillances de liaison et de chargement.  Autrement dit, si une tentative de chargement d'un assembly échoue, les demandes ultérieures de chargement du même assembly échouent immédiatement, sans aucune tentative de localisation de l'assembly.  Cet élément désactive ce comportement par défaut pour les échecs de liaison qui se produisent parce que l'assembly n'a pas pu être trouvé dans le chemin d'accès de détection.  Ces défaillances lèvent <xref:System.IO.FileNotFoundException>.  
  
 Quelques défaillances de liaison et de chargement ne sont pas affectées par cet élément et sont toujours mises en cache.  Ces défaillances se produisent parce que l'assembly a été trouvé mais n'a pas pu être chargé.  Ils lèvent <xref:System.BadImageFormatException> ou <xref:System.IO.FileLoadException>.  La liste suivante inclut quelques exemples de ces défaillances.  
  
-   Si vous essayez de charger un fichier qui n'est pas un assembly valide, les tentatives suivantes de chargement de l'assembly échoueront même si le fichier incorrect est remplacé par l'assembly correct.  
  
-   Si vous essayez de charger un assembly verrouillé par le fichier système, les tentatives suivantes de chargement de l'assembly échoueront même après que l'assembly soit lancée par le fichier système.  
  
-   Si une ou plusieurs versions de l'assembly que vous essayez de charger sont dans le chemin d'accès d'interrogation, mais la version spécifique que vous demandez n'est pas parmi eux, les tentatives suivantes pour charger cette version échoueront même si la version correcte est déplacée dans le chemin d'accès d'interrogation.  
  
## Exemple  
 L'exemple de code suivant indique comment désactiver la mise en cache des défaillances de liaison d'assembly qui se produisent parce que l'assembly est resté introuvable lors de la détection.  
  
```  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)