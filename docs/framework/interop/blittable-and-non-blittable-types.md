---
title: types blittable et non blittable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68e1d66b615db7369d71f56b402c13ce41ad5e54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="blittable-and-non-blittable-types"></a>types blittable et non blittable
La plupart des types de données ont une représentation commune à la fois dans la mémoire managée et non managée, et ne nécessitent pas de traitement particulier par le marshaleur d’interopérabilité. Ces types sont appelés *types blittables*, car ils ne nécessitent pas de conversion quand ils transitent entre le code managé et le code non managé.  
  
 Les structures qui sont retournées par les appels de code non managé doivent être des types blittables. L’appel de code non managé ne prend en charge aucune structure non blittable comme type de retour.  
  
 Les types suivants issus de l’espace de noms <xref:System> sont des types blittables :  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 Les types complexes suivants sont également des types blittables :  
  
-   Tableaux unidimensionnels de types blittables, comme un tableau d’entiers. Toutefois, un type qui contient un tableau de variables de types blittables n’est pas lui-même blittable.  
  
-   Types valeur mis en forme qui ne contiennent que des types blittables (et des classes s’ils sont marshalés comme types mis en forme). Pour plus d’informations sur les types valeur mis en forme, consultez [Marshaling par défaut pour les types valeur](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).  
  
 Les références d’objets ne sont pas blittables. Cela inclut un tableau de références aux objets qui sont blittables en eux-mêmes. Par exemple, vous pouvez définir une structure blittable, mais vous ne pouvez pas définir un type blittable contenant un tableau de références à ces structures.  
  
 Par souci d’optimisation, les tableaux de types et de classes blittables qui ne contiennent que des membres blittables sont [épinglés](../../../docs/framework/interop/copying-and-pinning.md) au lieu d’être copiés lors du marshaling. Ces types semblent être marshalés en tant que paramètres en entrée/sortie quand l’appelant et l’appelé résident dans le même cloisonnement. Cependant, ces types sont en fait marshalés en tant que paramètres en entrée et vous devez appliquer les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> si vous voulez marshaler l’argument en tant que paramètre en entrée/sortie.  
  
 Certains types de données managés requièrent une représentation différente dans un environnement non managé. Ces types de données non blittables doivent être convertis sous une forme qui peut être marshalée. Par exemple, les chaînes managées sont des types non blittables parce qu’elles doivent être converties en objets String avant de pouvoir être marshalées.  
  
 Le tableau suivant répertorie des types non blittables issus de l’espace de noms <xref:System>. Les [délégués](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), qui sont des structures de données qui réfèrent à une méthode statique ou à une instance de classe, sont également non blittables.  
  
|Type non blittable|Description|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.Boolean](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|Convertit en valeur de 1, 2 ou 4 octets, la valeur `true` ayant pour valeur 1 ou -1.|  
|[System.Char](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|Convertit en caractère ANSI ou Unicode.|  
|[System.Class](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|Convertit en interface de classe.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Convertit en interface ou en variant.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Convertit en chaîne se terminant par une référence null ou en BSTR.|  
|[System.Valuetype](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|Convertit en structure avec une disposition de mémoire fixe.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
  
 Les types d’objets et de classes sont pris en charge uniquement par COM Interop. Pour obtenir les types correspondants en [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# et C++, consultez [Vue d’ensemble de la bibliothèque de classes .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comportement de marshaling par défaut](../../../docs/framework/interop/default-marshaling-behavior.md)
