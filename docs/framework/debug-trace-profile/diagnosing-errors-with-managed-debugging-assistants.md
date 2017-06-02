---
title: "Diagnosing Errors with Managed Debugging Assistants | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHMDA"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "run-time error debugging"
  - "managed code, run-time debugging"
  - "resource debugging"
  - "registry, MDAs"
  - "common language runtime, debugging"
  - "MDAs (managed debugging assistants)"
  - "configuration files [.NET Framework], debugging runtime events"
  - "messages, managed debugging assistants"
  - "application configuration files, managed debugging assistants"
  - "debugging [.NET Framework], managed debugging assistants"
  - "environment variables, MDAs"
  - "access violation debugging [.NET Framework]"
  - "diagnostics, managed debugging assistants"
  - "unmanaged code, run-time debugging"
  - "default debug output stream"
  - "memory, debugging"
  - "app.config files, managed debugging assistants"
  - "managed debugging assistants (MDAs)"
  - "debugging [.NET Framework], run-time errors"
  - "trapping events"
  - "runtime, error debugging"
  - "disabling MDAs"
  - "output, managed debugging assistants"
  - "errors [.NET Framework], managed debugging assistants"
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: 63
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 63
---
# Diagnosing Errors with Managed Debugging Assistants
Les Assistants Débogage managé sont des aides au débogage qui fonctionnent conjointement avec le Common Language Runtime \(CLR\) pour fournir des informations sur l'état d'exécution.  Les Assistants génèrent des messages d'information sur les événements du runtime que vous ne pouvez pas intercepter en temps normal.  Vous pouvez utiliser les Assistants Débogage managé pour isoler les bogues d'application difficiles à déceler qui se produisent pendant les phases de transition entre un code managé et un code non managé.  Vous pouvez activer ou désactiver tous les Assistants Débogage managé en ajoutant une clé au Registre Windows ou en définissant une variable d'environnement.  Vous pouvez activer des Assistants Débogage managé spécifiques à l'aide de paramètres de configuration d'application.  Vous pouvez définir des paramètres de configuration supplémentaires pour certains Assistants Débogage managé dans le fichier de configuration de l'application.  Comme ces fichiers de configuration sont analysés au chargement du runtime, vous devez activer l'Assistant Débogage managé avant que l'application managée ne démarre.  Vous ne pouvez pas l'activer pour les applications qui ont déjà démarré.  
  
> [!NOTE]
>  Quand un Assistant Débogage managé est activé, il est actif même si votre code n'est pas en cours d'exécution sous un débogueur.  Si un événement d'Assistant Débogage managé est déclenché en l'absence de débogueur, le message de l'événement est présenté dans une boîte de dialogue d'exception non gérée, bien qu'il ne s'agisse pas d'une exception non gérée.  Pour éviter l'affichage de la boîte de dialogue, supprimez les paramètres de désactivation de l'Assistant Débogage managé quand votre code ne s'exécute pas dans un environnement de débogage.  
  
> [!NOTE]
>  Quand votre code s'exécute dans l'environnement de développement intégré \(IDE\) de Visual Studio, vous pouvez éviter la boîte de dialogue d'exception qui apparaît pour des événements d'Assistant Débogage managé spécifiques.  Pour ce faire, dans le menu **Déboguer**, cliquez sur **Exceptions**.  \(Si le menu **Déboguer** ne contient pas la commande **Exceptions**, cliquez sur **Personnaliser** dans le menu **Outils** pour ajouter cette commande.\) Dans la boîte de dialogue **Exceptions**, développez la liste **Assistants Débogage managé**, puis décochez la case **Levé** pour l'Assistant Débogage managé concerné.  Par exemple, pour éviter la boîte de dialogue d'exception pour un [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md), décochez la case **Levé** en regard de son nom dans la liste **Assistants Débogage managé**.  Vous pouvez également utiliser cette boîte de dialogue pour activer l'affichage des boîtes de dialogue d'exception des Assistants Débogage managé.  
  
 Le tableau suivant répertorie les Assistants Débogage managé fournis avec le .NET Framework.  
  
|||  
|-|-|  
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 Par défaut, le .NET Framework active une partie des Assistants Débogage managé pour tous les débogueurs managés.  Vous pouvez afficher l'ensemble par défaut dans Visual Studio en cliquant sur **Exceptions** dans le menu **Déboguer** et en développant la liste **Assistants Débogage managé**.  
  
## Activation et désactivation des Assistants Débogage managé  
 Vous pouvez activer et désactiver les Assistants Débogage managé en utilisant une clé de Registre, une variable d'environnement et des paramètres de configuration d'application.  Vous devez activer la clé de Registre ou la variable d'environnement pour utiliser les paramètres de configuration d'application.  
  
 Dans Visual Studio 2005 et versions ultérieures, quand le processus d'hébergement est activé, vous ne pouvez pas désactiver les Assistants Débogage managé qui se trouvent dans l'ensemble par défaut ou activer les Assistants Débogage managé qui ne s'y trouvent pas.  Le processus d'hébergement étant activé par défaut, il doit être désactivé explicitement.  
  
 Pour désactiver le processus d'hébergement dans Visual Studio, procédez comme suit :  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     La fenêtre **Concepteur de projets** apparaît.  
  
3.  Cliquez sur l'onglet **Déboguer**.  
  
4.  Dans la section **Activer les débogueurs**, décochez la case **Activer le processus d'hébergement Visual Studio**.  
  
 Toutefois, notez que la désactivation du processus d'hébergement peut affecter les performances.  Pour éviter de désactiver les Assistants Débogage managé, vous pouvez empêcher Visual Studio d'afficher la boîte de dialogue d'Assistant Débogage managé chaque fois qu'une notification d'Assistant Débogage managé est reçue.  Pour ce faire, cliquez sur **Exceptions** dans le menu **Déboguer**, développez la liste **Assistants Débogage managé**, puis cochez ou décochez la case **Levé** pour l'Assistant Débogage managé concerné.  
  
### Activation et désactivation des Assistants Débogage managé à l'aide d'une clé de Registre  
 Vous pouvez activer les Assistants Débogage managé en ajoutant la sous\-clé HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\MDA \(type REG\_SZ, valeur 1\) au Registre Windows.  Copiez l'exemple suivant dans un fichier texte nommé MDAEnable.reg.  Ouvrez l'Éditeur du Registre Windows \(RegEdit.exe\) et, dans le menu **Fichier**, choisissez **Importer**.  Sélectionnez le fichier MDAEnable.reg pour activer les Assistants Débogage managé sur cet ordinateur.  Définir la sous\-clé sur la valeur de chaîne 1 \(pas sur la valeur DWORD 1\) active la lecture des paramètres d'Assistant Débogage managé depuis le fichier *nom\_application.suffixe*.mda.config.  \(Par exemple, le fichier de configuration d'Assistant Débogage managé pour le Bloc\-notes porterait le nom notepad.exe.mda.config.\)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
  
```  
  
 Si l'ordinateur exécute une application 32 bits sur un système d'exploitation 64 bits, la clé MDA doit être définie comme suit :  
  
```  
Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
  
```  
  
 Pour plus d'informations, voir [Activation et désactivation des Assistants Débogage managé à l'aide de paramètres de configuration spécifiques à l'application](#appConfig).  Le paramétrage du Registre peut être remplacé par la variable d'environnement COMPLUS\_MDA.  Pour plus d'informations, voir [Activation et désactivation des Assistants Débogage managé à l'aide d'une variable d'environnement](#envVariable).  
  
 Pour désactiver les Assistants Débogage managé, définissez la sous\-clé MDA sur 0 \(zéro\) à l'aide de l'Éditeur du Registre Windows.  
  
 Par défaut, certains Assistants Débogage managé sont activés quand vous exécutez une application qui est attachée à un débogueur, même sans que la clé de Registre soit ajoutée.  Parmi ces Assistants figurent [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) et [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).  Vous pouvez désactiver ces Assistants en exécutant le fichier MDADisable.reg, comme indiqué précédemment dans cette section.  
  
<a name="envVariable"></a>   
### Activation et désactivation des Assistants Débogage managé à l'aide d'une variable d'environnement  
 L'activation des Assistants Débogage managé peut également être contrôlée par la variable d'environnement COMPLUS\_MDA, qui remplace la clé de Registre.  La chaîne COMPLUS\_MDA est une liste de noms d'Assistant Débogage managé ou d'autres chaînes de contrôle spéciales séparés par des points\-virgules et sans distinction minuscules\/majuscules.  Démarrer sous un débogueur managé ou non managé active par défaut un ensemble d'Assistants Débogage managé.  Pour ce faire, la valeur de la variable d'environnement ou de la clé de Registre doit être implicitement ajoutée au début de la liste délimitée par des points\-virgules qui répertorie les Assistants Débogage managé activés par défaut sous les débogueurs.  Les chaînes de contrôle spéciales sont les suivantes :  
  
-   `0` : désactive tous les Assistants Débogage managé.  
  
-   `1` : lit les paramètres d'Assistant Débogage managé dans le fichier *nom\_application*.mda.config.  
  
-   `managedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable managé est démarré sous un débogueur.  
  
-   `unmanagedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable non managé est démarré sous un débogueur.  
  
 En cas de conflit de paramètres, les paramètres les plus récents remplacent les paramètres antérieurs :  
  
-   `COMPLUS_MDA=0` désactive tous les Assistants Débogage managé, y compris ceux qui sont implicitement activés sous un débogueur.  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged` active `gcUnmanagedToManaged` outre tout Assistant Débogage managé implicitement activé sous un débogueur.  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged` active `gcUnmanagedToManaged`, mais désactive tout Assistant Débogage managé implicitement activé sous un débogueur.  
  
<a name="appConfig"></a>   
### Activation et désactivation des Assistants Débogage managé à l'aide de paramètres de configuration spécifiques à l'application  
 Vous pouvez activer, désactiver et configurer certains Assistants séparément dans le fichier de configuration d'Assistant Débogage managé propre à l'application.  Vous ne pouvez utiliser un fichier de configuration d'application pour configurer des Assistants Débogage managé que si la clé de Registre MDA ou la variable d'environnement COMPLUS\_MDA est définie.  En règle générale, le fichier de configuration d'application se trouve dans le même répertoire que le fichier exécutable \(.exe\) de l'application.  Le format du nom de fichier est *nom\_application*.mda.config ; par exemple, notepad.exe.mda.config.  Les Assistants qui sont activés dans le fichier de configuration d'application peuvent avoir des attributs ou des éléments qui permettent de contrôler le comportement de l'Assistant concerné.  L'exemple suivant illustre l'activation et la configuration de l'[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).  
  
```  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 L'Assistant Débogage managé `Marshaling` émet des informations sur le type managé qui est marshalé en un type non managé pour chaque transition de code managé vers un code non managé dans l'application.  L'Assistant Débogage managé `Marshaling` peut également filtrer les noms des champs de méthode et de structure fournis dans les éléments enfants `<methodFilter>` et `<fieldFilter>`, respectivement.  
  
 L'exemple suivant illustre l'activation de plusieurs Assistants Débogage managé à l'aide de leurs paramètres par défaut.  
  
```  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  Quand vous spécifiez plusieurs Assistants dans un fichier de configuration, vous devez les répertorier dans l'ordre alphabétique.  Par exemple, pour activer les Assistants Débogage managé `virtualCERCall` et `invalidCERCall`, vous devez ajouter l'entrée `<invalidCERCall />` avant l'entrée `<virtualCERCall />`.  Si vous n'indiquez pas les entrées dans l'ordre alphabétique, vous obtenez un message d'exception non gérée liée à un fichier de configuration non valide.  
  
### Sortie de l'Assistant Débogage managé  
 La sortie de l'Assistant Débogage managé est similaire à l'exemple suivant, qui illustre la sortie de l'Assistant Débogage managé `pInvokeStackImbalance`.  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack.  This is likely because the managed PInvoke signature does not match the unmanaged target signature.  Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## Voir aussi  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)