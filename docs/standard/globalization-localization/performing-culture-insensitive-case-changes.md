---
title: "Ex&#233;cution de changements de casse ind&#233;pendants de la culture | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "String.ToLower (méthode)"
  - "culture, respect de la casse"
  - "Char.ToLower (méthode)"
  - "casse, changement dans les chaînes indépendantes de la culture"
  - "Char.ToUpper (méthode)"
  - "opérations de chaînes indépendantes de la culture, changements de casse"
  - "String.ToUpper (méthode)"
  - "culture (paramètre)"
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Ex&#233;cution de changements de casse ind&#233;pendants de la culture
Les méthodes <xref:System.String.ToUpper%2A?displayProperty=fullName>, <xref:System.String.ToLower%2A?displayProperty=fullName>, <xref:System.Char.ToUpper%2A?displayProperty=fullName>et <xref:System.Char.ToLower%2A?displayProperty=fullName> fournissent des surcharges qui n'acceptent pas de paramètres.  Par défaut, ces surcharges sans paramètre effectuent des changements de casse basés sur la valeur de <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  Les résultats obtenus respectent la casse et peuvent varier en fonction de la culture.  Pour indiquer clairement que vous souhaitez que les changements de casse soient dépendants ou indépendants de la culture, vous devez utiliser les surcharges de ces méthodes qui exigent que vous indiquiez explicitement un paramètre `culture`.  Pour les changements de casse dépendants de la culture, spécifiez `CultureInfo.CurrentCulture` pour le paramètre `culture`.  Pour les changements de casse indépendants de la culture, spécifiez `CultureInfo.InvariantCulture` pour le paramètre `culture`.  
  
 Souvent, les chaînes sont converties dans une casse standard pour faciliter les recherches ultérieures.  Lorsque les chaînes sont utilisées de cette manière, vous devez spécifier `CultureInfo.InvariantCulture` pour le paramètre `culture`, car la valeur de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> peut changer entre le moment où la casse est modifiée et le moment où la recherche est effectuée.  
  
 Si une décision de sécurité est basée sur une opération de changement de casse, cette opération doit être indépendante de la culture pour garantir que le résultat n'est pas affecté par la valeur de `CultureInfo.CurrentCulture`.  Consultez la section « Comparaisons de chaînes qui utilisent la culture actuelle » de l'article [Meilleures pratiques pour l'utilisation de chaînes](../../../docs/standard/base-types/best-practices-strings.md) pour obtenir un exemple illustrant comment les comparaisons de chaînes dépendantes de la culture peuvent produire des résultats incohérents.  
  
## Utilisation des méthodes String.ToUpper et String.ToLower  
 Pour des raisons de clarté du code, il est recommandé de toujours utiliser des surcharges des méthodes `String.ToUpper` et `String.ToLower` qui vous permettent de spécifier un paramètre `culture` de manière explicite.  Par exemple, le code suivant recherche un identificateur.  L'opération `key.ToLower` est dépendante de la culture par défaut, mais ce comportement n'est pas clair à la lecture du code.  
  
### Exemple  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 Si vous voulez que l'opération `key.ToLower` soit indépendante de la culture, vous devez modifier l'exemple précédent comme suit, afin d'utiliser `CultureInfo.InvariantCulture` de manière explicite lors du changement de casse.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## Utilisation des méthodes Char.ToUpper et Char.ToLower  
 Même si les méthodes `Char.ToUpper` et `Char.ToLower` présentent les mêmes caractéristiques que les méthodes `String.ToUpper` et `String.ToLower`, les seules cultures affectées sont le turc \(Turquie\) et l'azerbaijani \(Latin, Azerbaïdjan\).  Ces deux cultures sont les seules qui présentent des différences de casse pour un même caractère.  Pour plus d'informations sur ce mappage de casse unique, consultez la section « casse » dans la rubrique de classe <xref:System.String>.  Pour des raisons de clarté du code et pour garantir des résultats cohérents, il est recommandé d'utiliser toujours les surcharges de ces méthodes qui vous permettent de spécifier un paramètre `culture` de manière explicite.  
  
## Voir aussi  
 <xref:System.String.ToUpper%2A?displayProperty=fullName>   
 <xref:System.String.ToLower%2A?displayProperty=fullName>   
 <xref:System.Char.ToUpper%2A?displayProperty=fullName>   
 <xref:System.Char.ToLower%2A?displayProperty=fullName>   
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)