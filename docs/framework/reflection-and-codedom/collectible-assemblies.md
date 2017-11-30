---
title: "Assemblys pouvant être collectés pour la génération de type dynamique"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Assemblys pouvant être collectés pour la génération de type dynamique

*Assemblys pouvant être collectés* sont des assemblys dynamiques qui peuvent être déchargés sans décharger le domaine d’application dans lequel ils ont été créés. Toute la mémoire managée et non managée utilisée par un assembly pouvant être collecté et les types qu’il contient peut être récupérée. Les informations telles que le nom de l’assembly sont supprimées des tables internes.

Pour activer le déchargement, utilisez le <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> indicateur lorsque vous créez un assembly dynamique. L’assembly est transitoire (autrement dit, il ne peut pas être enregistré) et est soumis aux limitations décrites dans le [Restrictions sur les assemblys pouvant être collectés](#restrictions-on-collectible-assemblies) section. Le common language runtime (CLR) décharge automatiquement un assembly pouvant être collecté lors de la version de tous les objets associés à l’assembly. Dans tous les autres égards, les assemblys pouvant être collectés sont créés et utilisés dans la même façon que les autres assemblys dynamiques.

## <a name="lifetime-of-collectible-assemblies"></a>Durée de vie des assemblys pouvant être collectés

La durée de vie d’un assembly pouvant être collecté est contrôlée par l’existence de références pour les types qu’il contient et les objets qui sont créés à partir de ces types. Le common language runtime ne décharge pas d’assembly tant qu’un ou plusieurs des éléments suivants existent (`T` correspond à tout type qui est défini dans l’assembly) : 

- Instance de `T`.

- Une instance d’un tableau de `T`.
 
- Une instance d’un type générique qui a `T` comme l’un de ses arguments de type. Cela inclut les collections génériques de `T`, même si cette collection est vide.

- Une instance de <xref:System.Type> ou <xref:System.Reflection.Emit.TypeBuilder> représentant `T`. 

   > [!IMPORTANT]
   > Vous devez libérer tous les objets qui représentent les parties de l’assembly. Le <xref:System.Reflection.Emit.ModuleBuilder> qui définit `T` conserve une référence à la <xref:System.Reflection.Emit.TypeBuilder>et le <xref:System.Reflection.Emit.AssemblyBuilder> objet conserve une référence à la <xref:System.Reflection.Emit.ModuleBuilder>, de sorte que les références à ces objets doivent être libérées. Même l’existence d’un <xref:System.Reflection.Emit.LocalBuilder> ou <xref:System.Reflection.Emit.ILGenerator> utilisé dans la construction de `T` empêche le déchargement.

- Une référence statique à `T` par un autre type défini dynamiquement `T1` qui est encore accessible par l’exécution de code. Par exemple, `T1` peuvent dériver de `T`, ou `T` peut être le type d’un paramètre dans une méthode de `T1`.
 
- A **ByRef** dans un champ statique qui appartient à `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, ou <xref:System.RuntimeMethodHandle> qui fait référence à `T` ou à un composant de `T`.

- Une instance de tout objet reflection qui peut être utilisé indirectement ou pour accéder directement à la <xref:System.Type> objet qui représente `T`. Par exemple, le <xref:System.Type> pour l’objet `T` peut être obtenu à partir d’un type de tableau dont le type d’élément est `T`, ou à partir d’un type générique qui a `T` comme argument de type. 

- Une méthode `M` sur la pile des appels de tout thread, où `M` est une méthode de `T` ou une méthode au niveau du module qui est définie dans l’assembly.

- Un délégué à une méthode statique qui est défini dans un module de l’assembly.

Si seul un élément de cette liste existe pour qu’un type ou une méthode dans l’assembly, le runtime ne peut pas décharger l’assembly.

> [!NOTE]
> Le runtime ne décharge pas réellement l’assembly jusqu'à ce que les finaliseurs ont été exécutés pour tous les éléments dans la liste.

À des fins de suivi de durée de vie, un type générique construit comme `List<int>` (en c#) ou `List(Of Integer)` (en Visual Basic), qui est créé et utilisé dans la génération d’un assembly pouvant être collecté est considérée comme ayant été défini dans l’assembly qui contient le type générique définition de type ou dans un assembly qui contient la définition de l’un de ses arguments de type. L’assembly exact utilisé est un détail d’implémentation et l’objet de modifications.
 
## <a name="restrictions-on-collectible-assemblies"></a>Restrictions sur les assemblys pouvant être collectés

Les restrictions suivantes s’appliquent aux assemblys pouvant être collectés : 

- **Références statiques**   
  Types dans un assembly dynamique simple ne peut pas avoir des références statiques à des types qui sont définis dans un assembly pouvant être collecté. Par exemple, si vous définissez un type simple qui hérite d’un type dans un assembly pouvant être collecté, une <xref:System.NotSupportedException> exception est levée. Un type dans un assembly pouvant être collecté peut avoir des références statiques à un type dans un autre assembly pouvant être collecté, mais cela permet d’étendre la durée de vie de l’assembly référencé à la durée de vie de l’assembly de référence.

- **Interopérabilité COM**   
   Les interfaces COM peuvent être définis dans un assembly pouvant être collecté, et aucune instance de types dans un assembly pouvant être collecté ne peut être convertis en objets COM. Un type dans un assembly pouvant être collecté ne peut pas servir en tant que callable wrapper CCW (COM) ou callable wrapper RCW (runtime). Toutefois, les types dans les assemblys pouvant être collectés peuvent utiliser des objets qui implémentent les interfaces COM.

- **Appel de plateforme**   
   Les méthodes qui ont le <xref:System.Runtime.InteropServices.DllImportAttribute> attribut compilera pas lorsqu’ils sont déclarés dans un assembly pouvant être collecté. Le <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> ne peut pas être utilisée dans l’implémentation d’un type dans un assembly pouvant être collecté, et ces types ne peut pas être marshalés en code non managé. Toutefois, vous pouvez appeler en code natif à l’aide d’un point d’entrée qui est déclaré dans un assembly non-pouvant être collecté.
 
- **Marshaling**   
   Objets (en particulier, les délégués) qui sont définis dans les assemblys pouvant être collectés ne peut pas être marshalés. Il s’agit d’une restriction sur tous les types émis transitoires.

- **Le chargement des assemblys**   
   Émission de réflexion est le seul mécanisme est pris en charge pour le chargement des assemblys pouvant être collectés. Les assemblys sont chargés à l’aide de toute autre forme de chargement d’assembly ne peut pas être déchargés.
 
- **Objets liés au contexte**    
   Les variables statiques de contexte ne sont pas pris en charge. Les types dans un assembly pouvant être collecté ne peut pas étendre <xref:System.ContextBoundObject>. Toutefois, code dans les assemblys pouvant être collectés peut utiliser des objets liés au contexte définis ailleurs.

- **Données statiques de thread**       
   Variables static de thread ne sont pas pris en charge.

## <a name="see-also"></a>Voir aussi

[Émission d’assemblys et de méthodes dynamiques](emitting-dynamic-methods-and-assemblies.md)
