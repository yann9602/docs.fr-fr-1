---
title: "Atténuation : Nouveau compilateur JIT 64 bits | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 994da1622246d09930fa9b74d6debac4f7a24b5b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Atténuation : Nouveau compilateur JIT 64 bits
À compter du .NET Framework 4.6, le runtime comprend un nouveau compilateur JIT 64 bits pour la compilation juste-à-temps. Ce changement n’affecte pas la compilation avec le compilateur JIT 32 bits.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Comportement inattendu ou exceptions  
 Dans certains cas, la compilation avec le nouveau compilateur JIT 64 bits entraîne une exception de runtime ou le non-respect du comportement lors de l’exécution de code compilé par l’ancien compilateur JIT 64 bits. Voici quelques-unes des différences connues :  
  
> [!IMPORTANT]
>  Tous ces problèmes connus ont été résolus dans le nouveau compilateur 64 bits fourni avec le SDK .NET Framework 4.6.2. La plupart ont également été résolus dans les versions de maintenance du .NET Framework 4.6 et 4.6.1, qui sont disponibles via Windows Update. Vous pouvez éviter ces problèmes en vous assurant que votre version de Windows est à jour, ou en mettant à niveau vers .NET Framework 4.6.2.  
  
-   Dans certaines conditions, une opération d’unboxing peut lever une <xref:System.NullReferenceException> dans les versions Release avec l’optimisation activée.  
  
-   Dans certains cas, l’exécution du code de production dans un corps de méthode volumineux peut lever une <xref:System.StackOverflowException>.  
  
-   Dans certaines conditions, les structures passées à une méthode sont traitées comme des types référence plutôt que des types valeur dans les versions Release. Ce problème se manifeste notamment lorsque des éléments dans une collection apparaissent dans un ordre inattendu.  
  
-   Dans certaines conditions, la comparaison de valeurs <xref:System.UInt16> avec le bit le plus élevé est incorrecte si l’optimisation est activée.  
  
-   Sous certaines conditions, en particulier lors de l’initialisation de tableaux de valeurs, l’initialisation de la mémoire par l’instruction <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=fullName> du langage intermédiaire peut initialiser la mémoire avec une valeur incorrecte. Cela peut entraîner une exception non gérée ou une sortie incorrecte.  
  
-   Dans certains cas rares, un test conditionnel binaire peut retourner une valeur <xref:System.Boolean> incorrecte ou lever une exception si les optimisations du compilateur sont activées.  
  
-   Sous certaines conditions, si une instruction `if` est utilisée pour tester une condition avant d’entrer dans un bloc `try` et dans la sortie du bloc `try`, et que la même condition est évaluée dans le bloc `catch` ou `finally`, le nouveau compilateur JIT 64 bits supprime la condition `if` du bloc `catch` ou `finally` lorsqu’il optimise le code. Par conséquent, le code à l’intérieur de l’instruction `if` dans le bloc `catch` ou `finally` est exécuté de manière non conditionnelle.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Atténuation des problèmes connus  
 Si vous rencontrez les problèmes répertoriés ci-dessus, vous pouvez les traiter en procédant d’une des façons suivantes :  
  
-   Mettez à niveau vers .NET Framework 4.6.2. Le nouveau compilateur 64 bits inclus avec .NET Framework 4.6.2 résout chacun de ces problèmes connus.  
  
-   Assurez-vous que votre version de Windows est à jour en exécutant Windows Update. Les mises à jour de service pour .NET Framework 4.6 et 4.6.1 corrigent chacun de ces problèmes, à l’exception de <xref:System.NullReferenceException> dans une opération d’unboxing.  
  
-   Compilez avec l’ancien compilateur JIT 64 bits. Consultez la section [Atténuation des autres problèmes](#Other) pour plus d’informations sur cette procédure.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Atténuation des autres problèmes  
 Si vous rencontrez une autre différence de comportement entre le code compilé avec l’ancien compilateur JIT 64 bits et celui compilé avec le nouveau compilateur, ou entre les versions Debug et Release de votre application lorsque les deux sont compilées avec le nouveau compilateur JIT 64 bits, vous pouvez procéder comme suit pour compiler votre application avec l’ancien compilateur JIT 64 bits :  
  
-   Pour chaque application le nécessitant, vous pouvez ajouter l’élément [ \<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) au fichier de configuration de votre application. Ce qui suit désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise l’ancien compilateur à la place.  
  
    ```xml  
  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJIT enabled="1" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   Pour chaque utilisateur concerné, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`. La valeur 1 active l’ancien compilateur JIT 64 bits ; la valeur 0 le désactive et active le nouveau compilateur JIT 64 bits.  
  
-   Pour chaque machine concernée, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`. La valeur 1 active l’ancien compilateur JIT 64 bits ; la valeur 0 le désactive et active le nouveau compilateur JIT 64 bits.  
  
 Vous pouvez également nous indiquer votre problème en signalant un bogue sur [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)   
 [Élément \<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
