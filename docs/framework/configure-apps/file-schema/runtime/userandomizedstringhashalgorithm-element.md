---
title: "&lt;UseRandomizedStringHashAlgorithm&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6231f362a30f4766ccf5a43d33fa0dc7257ad57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;UseRandomizedStringHashAlgorithm&gt; élément
Détermine si le common language runtime calcule les codes de hachage de chaînes sur un par domaine d’application.  
  
 \<configuration>  
\<runtime >  
\<UseRandomizedStringHashAlgorithm >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si les codes de hachage pour les chaînes sont calculés sur un par domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`0`|Le common language runtime ne calcule pas les codes de hachage de chaînes sur un par domaine d’application ; un seul algorithme est utilisé pour calculer les codes de hachage de chaîne. Il s'agit de la valeur par défaut.|  
|`1`|Le common language runtime calcule les codes de hachage de chaînes sur un par domaine d’application. Chaînes identiques dans différents domaines d’application et dans différents processus aura des codes de hachage différent.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, le <xref:System.StringComparer> classe et <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> la méthode utilise un seul algorithme de hachage qui génère un code de hachage cohérent entre domaines d’application. Cela revient à affecter la `enabled` attribut de la `<UseRandomizedStringHashAlgorithm>` élément `0`. Il s’agit d’algorithme de hachage utilisé dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 Le <xref:System.StringComparer> classe et le <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode peut également utiliser un autre algorithme de hachage qui calcule les codes de hachage sur un par domaine d’application. Par conséquent, les codes de hachage pour les chaînes équivalentes sont différentes entre domaines d’application. Il s’agit d’une fonctionnalité d’abonnement ; Pour en bénéficier, vous devez définir le `enabled` attribut de la `<UseRandomizedStringHashAlgorithm>` élément `1`.  
  
 La recherche de chaîne dans une table de hachage est généralement une opération o (1). Toutefois, lorsqu’un grand nombre de collisions se produire, la recherche peut devenir un O (n<sup>2</sup>) opération. Vous pouvez utiliser la `<UseRandomizedStringHashAlgorithm>` élément de configuration pour générer un algorithme de hachage aléatoire par domaine d’application, qui à son tour limite le nombre de collisions potentielles, en particulier lorsque les clés à partir de laquelle les codes de hachage sont calculées reposent sur les données d’entrée par les utilisateurs.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un `DisplayString` classe qui inclut une constante de chaîne privée, `s`, dont la valeur est « Il s’agit d’une chaîne. » Il inclut également un `ShowStringHashCode` méthode qui affiche la valeur de chaîne et son code de hachage, ainsi que le nom du domaine d’application dans lequel la méthode s’exécute.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Lorsque vous exécutez l’exemple sans fournir un fichier de configuration, il affiche une sortie similaire à ce qui suit. Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d’application.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple et exécutez l’exemple, les codes de hachage pour la même chaîne diffèrent par domaine d’application.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Lorsque le fichier de configuration est présent, l’exemple affiche la sortie suivante :  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
