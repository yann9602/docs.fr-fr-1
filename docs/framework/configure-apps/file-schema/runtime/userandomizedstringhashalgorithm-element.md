---
title: "&lt;UseRandomizedStringHashAlgorithm&gt;, &#201;l&#233;ment | Microsoft Docs"
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
helpviewer_keywords: 
  - "<UseRandomizedStringHashAlgorithm> (élément)"
  - "UseRandomizedStringHashAlgorithm (élément)"
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;UseRandomizedStringHashAlgorithm&gt;, &#201;l&#233;ment
Détermine si le Common Langage Runtime calcule des codes de hachage pour les chaînes par domaine d'application.  
  
## Syntaxe  
  
```  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les codes de hachage pour les chaînes sont calculés par domaine d'application.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`0`|Le Common Langage Runtime ne calcule pas les codes de hachage des chaînes par domaine d'application ; un seul algorithme est utilisé pour calculer les codes de hachage des chaînes.  Valeur par défaut.|  
|`1`|Le Common Langage Runtime calcule les codes de hachage pour les chaînes par domaine d'application.  Les chaînes identiques dans des domaines d'application différents et dans des processus différents ont différents codes de hachage.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Par défaut, la classe <xref:System.StringComparer> et la méthode <xref:System.String.GetHashCode%2A?displayProperty=fullName> utilisent un algorithme de hachage unique qui produit un code de hachage cohérent dans les domaines d'application.  Cela revient à définir l'attribut `enabled` de l'élément `<UseRandomizedStringHashAlgorithm>` sur `0`.  Il s'agit de l'algorithme de hachage utilisé dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 La classe <xref:System.StringComparer> et la méthode <xref:System.String.GetHashCode%2A?displayProperty=fullName> peuvent également utiliser un algorithme de hachage différent qui calcule les codes de hachage par domaine d'application.  Par conséquent, les codes de hachage pour des chaînes équivalentes diffèreront entre des domaines d'application.  Il s'agit d'une fonctionnalité déclarative. Pour en tirer parti, vous devez définir l'attribut `enabled` de l'élément `<UseRandomizedStringHashAlgorithm>` sur `1`.  
  
 La recherche de chaîne dans une table de hachage est généralement une opération O\(1\).  Toutefois, lorsque de nombreuses collisions se produisent, la recherche peut devenir une opération O\(n<sup>2</sup>\).  Vous pouvez utiliser l'élément de configuration `<UseRandomizedStringHashAlgorithm>` pour générer un algorithme de hachage aléatoire par domaine d'application, qui limite à son tour le nombre de collisions potentielles, en particulier lorsque les clés à partir desquelles les codes de hachage sont calculés sont basées sur la saisie de données par les utilisateurs.  
  
## Exemple  
 L'exemple suivant définit une classe `DisplayString` qui inclut une constante de chaîne privée, `s`, dont la valeur est « Ceci est une chaîne ». Il inclut également une méthode `ShowStringHashCode` qui affiche la valeur de chaîne et son code de hachage avec le nom du domaine d'application dans lequel la méthode est exécutée.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Lorsque vous exécutez l'exemple sans fournir un fichier de configuration, il affiche une sortie similaire à la suivante.  Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d'application.  
  
```  
  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l'exemple, puis exécutez l'exemple, les codes de hachage pour la même chaîne diffèrent par domaine d'application.  
  
```  
  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
  
```  
  
 Lorsque le fichier de configuration est présent, l'exemple affiche la sortie suivante :  
  
```  
  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
  
```  
  
## Voir aussi  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.String.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>