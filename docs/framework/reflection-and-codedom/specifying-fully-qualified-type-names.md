---
title: "Sp&#233;cification des noms de types qualifi&#233;s complets | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), noms"
  - "Backus-Naur (forme)"
  - "BNF"
  - "noms de types qualifiés complets"
  - "IDENTIFIER"
  - "langages, BNF (syntaxe)"
  - "noms (.NET Framework), assemblys"
  - "noms (.NET Framework), noms de types qualifiés complets"
  - "réflexion, noms de types qualifiés complets"
  - "caractères spéciaux"
  - "jetons"
  - "noms de types"
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Sp&#233;cification des noms de types qualifi&#233;s complets
Vous devez spécifier des noms de types pour pouvoir valider l'entrée servant aux diverses opérations de réflexion.  Un nom de type qualifié complet se compose d'une spécification de nom d'assembly, d'une spécification d'espace de noms et d'un nom de type.  Les spécifications de noms de types sont utilisées par les méthodes telles que <xref:System.Type.GetType%2A?displayProperty=fullName>, <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> et <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>.  
  
## Syntaxe de forme Backus\-Naur pour les noms de types  
 La forme Backus\-Naur \(BNF\) définit la syntaxe des langages formels.  Le tableau suivant décrit les règles lexicales BNF permettant de reconnaître une entrée valide.  Les éléments terminaux \(éléments qui ne peuvent pas être réduits davantage\) sont affichés tout en majuscules.  Les éléments non terminaux \(ces éléments qui peuvent être réduits davantage\) sont affichés dans une casse mixte ou entre des guillemets simples ; toutefois, le guillemet simple \('\) ne fait pas partie de la syntaxe proprement dite.  Le symbole de canal \(&#124;\) signale des règles qui possèdent des sous\-règles.  
  
|Syntaxe BNF des noms de types qualifiés complets|  
|------------------------------------------------------|  
|TypeSpec                          :\=   ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec            :\=   SimpleTypeSpec '&'|  
|SimpleTypeSpec                :\=   PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec                :\=   SimpleTypeSpec '\*'|  
|ArrayTypeSpec                  :\=   SimpleTypeSpec '\[ReflectionDimension\]'<br /><br /> &#124;     SimpleTypeSpec '\[ReflectionEmitDimension\]'|  
|ReflectionDimension           :\=   '\*'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension    :\=   '\*'<br /><br /> &#124;     Number '..' Nombre<br /><br /> &#124;     Number '…'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|Number                            :\=   \[0\-9\]\+|  
|TypeName                         :\=   NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName ',' AssemblyNameSpec|  
|NamespaceTypeName        :\=   NestedTypeName<br /><br /> &#124;     NamespaceSpec '.' NestedTypeName|  
|NestedTypeName               :\=   IDENTIFICATEUR<br /><br /> &#124;     NestedTypeName '\+' IDENTIFIER|  
|NamespaceSpec                 :\=   IDENTIFICATEUR<br /><br /> &#124;     NamespaceSpec '.' IDENTIFIER|  
|AssemblyNameSpec           :\=   IDENTIFICATEUR<br /><br /> &#124;     IDENTIFIER ',' AssemblyProperties|  
|AssemblyProperties            :\=   AssemblyProperty<br /><br /> &#124;     AssemblyProperties ',' AssemblyProperty|  
|AssemblyProperty              :\=   AssemblyPropertyName '\=' AssemblyPropertyValue|  
  
## Spécification des caractères spéciaux  
 Dans un nom de type, IDENTIFICATEUR correspond à n'importe quel nom valide déterminé par les règles d'un langage.  
  
 Utilisez la barre transversale \(\\\) comme caractère d'échappement pour séparer les jetons suivants lorsqu'ils sont utilisés avec l'IDENTIFICATEUR.  
  
|Jeton|Signification|  
|-----------|-------------------|  
|\\,|Séparateur d'assembly.|  
|\\\+|Séparateur de type imbriqué.|  
|\\&|Type référence.|  
|\\\*|Type pointeur.|  
|\\\[|Délimiteur de dimension du tableau.|  
|\\\]|Délimiteur de dimension du tableau.|  
|\\.|Utilisez la barre oblique inverse avant un point uniquement si celui\-ci est utilisé dans une spécification de tableau.  Les points de NamespaceSpec ne sont pas précédés d'une barre oblique inverse.|  
|\\\\|Barre oblique inverse requise en tant que littéral de chaîne.|  
  
 Remarquez que dans tous les composants TypeSpec exceptés AssemblyNameSpec, les espaces peuvent être utilisés.  Dans AssemblyNameSpec, les espaces précédant le séparateur ',' peuvent être utilisés, mais ceux situés après le séparateur ',' sont ignorés.  
  
 Les classes Reflection, telles que <xref:System.Type.FullName%2A?displayProperty=fullName>, retournent le nom tronqué, lequel peut être utilisé dans un appel à <xref:System.Type.GetType%2A>, par exemple, `MyType.GetType(myType.FullName)`.  
  
 Par exemple, le nom qualifié complet d'un type peut être `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.  
  
 Si l'espace de noms est `Ozzy.Out+Back`, le signe plus \(\+\) doit être précédé d'une barre oblique inverse.  Sinon, l'analyseur l'interprète comme un séparateur d'imbrication.  La réflexion génère cette chaîne sous la forme suivante : `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.  
  
## Spécification des noms d'assemblys  
 L'information minimale requise dans une spécification de nom d'assembly est le nom textuel \(IDENTIFICATEUR\) de l'assembly.  Vous pouvez faire suivre l'IDENTIFICATEUR d'une liste de paires de propriétés\/valeurs avec la virgule comme séparateur, comme l'illustre le tableau suivant.  L'affectation d'un nom à l'IDENTIFICATEUR doit se conformer aux règles de dénomination de fichier.  L'IDENTIFICATEUR ne respecte pas la casse.  
  
|Nom de propriété|Description|Valeurs autorisées|  
|----------------------|-----------------|------------------------|  
|**Version**|Numéro de version de l'assembly|*Major.Minor.Build.Revision*, où *Major*, *Minor*, *Build* et *Revision* sont des entiers compris entre 0 et 65 535 inclus.|  
|**PublicKey**|Clé publique complète|Valeur de chaîne de la clé publique complète au format hexadécimal.  Spécifiez une référence null \(**Nothing** en Visual Basic\) pour indiquer explicitement un assembly privé.|  
|**PublicKeyToken**|Jeton de clé publique \(hachage de 8 octets de la clé publique complète\)|Valeur de chaîne du jeton de clé publique au format hexadécimal.  Spécifiez une référence null \(**Nothing** en Visual Basic\) pour indiquer explicitement un assembly privé.|  
|**Culture**|Culture d'assembly|Culture de l'assembly au format RFC\-1766 ou « neutre » pour les assemblys indépendants des langages \(non\-satellites\).|  
|**Personnalisé**|Objet binaire volumineux \(BLOB\) personnalisé.  Utilisé uniquement dans les assemblys générés par le [générateur d'images natives \(Ngen\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Chaîne personnalisée utilisée par le générateur d'images natives \(Ngen\) pour informer le cache d'assembly que l'assembly installé est une image native, et que par conséquent il doit être installé dans le cache des images natives.  Autre dénomination : chaîne Zap.|  
  
 L'exemple suivant montre **AssemblyName** pour un assembly nommé simplement avec une culture par défaut.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 L'exemple suivant illustre une référence complète pour un assembly utilisant un nom fort et la culture « en ».  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui peut correspondre à un assembly portant un nom fort ou nommé simplement.  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly nommé simplement.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly portant un nom fort.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## Spécification des pointeurs  
 SimpleTypeSpec\* représente un pointeur non managé.  Par exemple, pour obtenir un pointeur vers le type MyType, utilisez `Type.GetType("MyType*")`.  Pour obtenir un pointeur vers un autre pointeur vers le type MyType, utilisez `Type.GetType("MyType**")`.  
  
## Spécification des références  
 SimpleTypeSpec & représente un pointeur ou une référence managés.  Par exemple, pour obtenir une référence vers le type MyType, utilisez `Type.GetType("MyType &")`.  Remarquez qu'à la différence des pointeurs, les références sont limitées à un seul niveau.  
  
## Spécification des tableaux  
 Dans la syntaxe BNF, ReflectionEmitDimension ne s'applique qu'aux définitions de types incomplètes récupérées à l'aide de <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName>.  Les définitions de types incomplètes sont des objets <xref:System.Reflection.Emit.TypeBuilder> construits à l'aide de [Reflection.Emit](frlrfSystemReflectionEmit) mais sur lesquels <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=fullName> n'a pas été appelé.  ReflectionDimension peut être utilisé pour récupérer une définition de type achevée, c'est\-à\-dire un type qui a été chargé.  
  
 Les tableaux sont accessibles par réflexion en spécifiant le rang d'un tableau :  
  
-   `Type.GetType("MyArray[]")` obtient un tableau unidimensionnel dont la limite inférieure est égale à 0.  
  
-   `Type.GetType("MyArray[*]")` obtient un tableau unidimensionnel dont la limite inférieure est inconnue.  
  
-   `Type.GetType("MyArray[][]")` obtient un tableau contenant un tableau à deux dimensions.  
  
-   `Type.GetType("MyArray[*,*]")` et `Type.GetType("MyArray[,]")` obtiennent un tableau rectangulaire à deux dimensions dont les limites inférieures sont inconnues.  
  
 Remarquez que du point de vue du runtime, `MyArray[] != MyArray[*]`, mais pour les tableaux multidimensionnels, les deux notations sont équivalentes.  En d'autres termes, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` prend la valeur **true**.  
  
 Pour **ModuleBuilder.GetType**, `MyArray[0..5]` indique un tableau unidimensionnel dont la taille est égale à 6 et la limite inférieure à 0. `MyArray[4…]` indique un tableau unidimensionnel dont la taille est inconnue et dont la limite inférieure est égale à 4.  
  
## Voir aussi  
 <xref:System.Reflection.AssemblyName>   
 <xref:System.Reflection.Emit.ModuleBuilder>   
 <xref:System.Reflection.Emit.TypeBuilder>   
 <xref:System.Type.FullName%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>   
 [Affichage des informations de type](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)