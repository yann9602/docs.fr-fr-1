---
title: "Exécution de changements de casse indépendants de la culture"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a>Exécution de changements de casse indépendants de la culture
Le <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> méthodes fournissent des surcharges qui n’acceptent pas de paramètres. Par défaut, ces surcharges sans paramètre effectuent des changements de casse basés sur la valeur de la <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Cela produit des résultats de la casse peuvent varier selon la culture. Pour indiquer clairement que vous souhaitez être dépendante ou indépendante de la culture des changements de casse, vous devez utiliser les surcharges de ces méthodes, vous devez spécifier explicitement un `culture` paramètre. Pour les changements de casse dépendante de la culture, spécifiez `CultureInfo.CurrentCulture` pour la `culture` paramètre. Pour les changements de casse indépendants de la culture, spécifiez `CultureInfo.InvariantCulture` pour la `culture` paramètre.  
  
 Souvent, les chaînes sont converties en une casse standard pour faciliter les recherches plus tard. Lorsque les chaînes sont utilisées de cette manière, vous devez spécifier `CultureInfo.InvariantCulture` pour le `culture` paramètre, car la valeur de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> peut changer entre le moment où la casse est modifiée et l’heure à laquelle la recherche est effectuée.  
  
 Si une décision de sécurité est basée sur une opération de changement de casse, l’opération doit être indépendante de la culture pour garantir que le résultat n’est pas affecté par la valeur de `CultureInfo.CurrentCulture`. Consultez la section « Chaîne comparaisons qui utiliser la Culture en cours » de la [meilleures pratiques pour l’utilisation de chaînes](../../../docs/standard/base-types/best-practices-strings.md) article pour obtenir un exemple qui montre comment des opérations de chaîne peut produire des résultats incohérents.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>À l’aide de la String.ToUpper et String.ToLower  
 Pour la clarté du code, il est recommandé de toujours utiliser des surcharges de la `String.ToUpper` et `String.ToLower` méthodes qui vous permettent de spécifier un `culture` paramètre explicitement. Par exemple, le code suivant effectue une recherche d’identificateur. Le `key.ToLower` opération est dépendante de la culture par défaut, mais ce comportement n’est pas clair à partir de la lecture du code.  
  
### <a name="example"></a>Exemple  
  
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
  
 Si vous souhaitez que le `key.ToLower` opération soit indépendante de la culture, vous devez modifier l’exemple précédent comme suit pour utiliser explicitement le `CultureInfo.InvariantCulture` lors de la modification de la casse.  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>À l’aide de la méthodes Char.ToUpper et Char.ToLower  
 Bien que le `Char.ToUpper` et `Char.ToLower` méthodes ont les mêmes caractéristiques que le `String.ToUpper` et `String.ToLower` méthodes, les seules cultures affectées sont le turc (Turquie) et Azérie (Latin, Azerbaïdjan). Il s’agit uniquement deux cultures avec des différences de casse de caractère unique. Pour plus d’informations sur ce mappage de casse unique, consultez la section « Casse » dans la <xref:System.String> rubrique de la classe. Pour la clarté du code et pour garantir des résultats cohérents, il est recommandé de toujours utiliser les surcharges de ces méthodes qui vous permettent de spécifier explicitement un `culture` paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
