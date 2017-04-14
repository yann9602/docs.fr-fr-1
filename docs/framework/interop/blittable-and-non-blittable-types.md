---
title: "Blittable and Non-Blittable Types | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "interop marshaling, blittable types"
  - "blittable types, interop marshaling"
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Blittable and Non-Blittable Types
La plupart des types de données ont une représentation commune à la fois dans la mémoire managée et non managée, et ne nécessitent pas de traitement particulier par le marshaleur d'interopérabilité.  Ces types sont appelés des *types blittables* car ils ne nécessitent pas de conversion lorsqu'ils sont passés entre le code managé et le code non managé.  
  
 Les structures qui sont retournées par les appels de code non managé doivent être des types blittables.  L'appel de code non managé ne prend en charge aucune structure non blittable comme types de retour.  
  
 Les types suivants issus de l'espace de noms <xref:System> sont des types blittables :  
  
-   <xref:System.Byte?displayProperty=fullName>  
  
-   <xref:System.SByte?displayProperty=fullName>  
  
-   <xref:System.Int16?displayProperty=fullName>  
  
-   <xref:System.UInt16?displayProperty=fullName>  
  
-   <xref:System.Int32?displayProperty=fullName>  
  
-   <xref:System.UInt32?displayProperty=fullName>  
  
-   <xref:System.Int64?displayProperty=fullName>  
  
-   <xref:System.UInt64?displayProperty=fullName>  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Single?displayProperty=fullName>  
  
-   <xref:System.Double?displayProperty=fullName>  
  
 Les types complexes suivants sont également des types blittables :  
  
-   Les tableaux unidimensionnels de types blittables tels qu'un tableau d'entiers.  Toutefois, un type qui contient un tableau de variables de types blittables n'est pas lui\-même blittable.  
  
-   Les types valeur mis en forme qui ne contiennent que des types blittables \(et des classes s'ils sont marshalés comme types mis en forme\).  Pour plus d'informations sur les types valeur mis en forme, consultez [Default Marshaling for Value Types](http://msdn.microsoft.com/fr-fr/4d9a876c-e05a-40ba-bd85-bd22877f984a).  
  
 Les références d'objets ne sont pas blittables.  Cela inclut un tableau de références aux objets qui sont blittables en eux\-mêmes.  Par exemple, vous pouvez définir une structure blittable, mais vous ne pouvez pas définir un type blittable contenant un tableau de références à ces structures.  
  
 Par souci d'optimisation, les tableaux de types et de classes blittables qui ne contiennent que des membres blittables sont [épinglés](../../../docs/framework/interop/copying-and-pinning.md) au lieu d'être copiés lors du marshaling.  Ces types semblent être marshalés en tant que paramètres en entrée\/sortie lorsque l'appelant et l'appelé résident dans le même apartment \(cloisonné\).  Cependant, ces types sont en fait marshalés en tant que paramètres en entrée et vous devez appliquer les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> si vous voulez marshaler l'argument en tant que paramètre en entrée\/sortie.  
  
 Certains types de données managées requièrent une représentation différente dans un environnement non managé.  Ces types de données non blittables doivent être convertis en un formulaire qui peut être marshalé.  Par exemple, les chaînes managées sont des types non blittables parce qu'ils doivent être convertis en objets de type chaîne avant qu'ils puissent être marshalés.  
  
 Le tableau suivant répertorie des types non blittables issus de l'espace de noms <xref:System> :  Les [Délégués](http://msdn.microsoft.com/fr-fr/d176ee76-f982-494b-b03d-92e4118896e2) qui sont des structures de données qui réfèrent à une méthode statique ou à une instance de classe, sont également non blittables.  
  
|Type non blittable|Description|  
|------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.Boolean](http://msdn.microsoft.com/fr-fr/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|Convertit en valeur de 1, 2, ou 4 octets, la valeur `true` ayant pour valeur 1 ou \-1.|  
|[System.Char](http://msdn.microsoft.com/fr-fr/cecc87c1-075e-4cde-aa56-33d189f66feb)|Convertit en caractère ANSI ou Unicode.|  
|[System.Class](http://msdn.microsoft.com/fr-fr/fe334af5-0123-43d8-be84-26f6f023ddb6)|Convertit en interface de classe.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Convertit en interface ou en variant.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Convertit en chaîne se terminant par une référence null ou BSTR.|  
|[System.Valuetype](http://msdn.microsoft.com/fr-fr/4d9a876c-e05a-40ba-bd85-bd22877f984a)|Convertit en structure avec une disposition en mémoire fixe.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
  
 Les types d'objets et de classes sont pris en charge uniquement par COM interop.  Pour obtenir les types correspondants dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C\# et C\+\+, consultez [Vue d'ensemble de la bibliothèque de classes](../../../docs/standard/class-library-overview.md).  
  
## Voir aussi  
 [Default Marshaling Behavior](../../../docs/framework/interop/default-marshaling-behavior.md)