---
title: "Interfaces de débogage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a>Interfaces de débogage
Cette section décrit les interfaces non managées qui gèrent le débogage d'un programme s'exécutant dans le Common Language Runtime (CLR).  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICLRDataEnumMemoryRegions (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Fournit une méthode pour énumérer les régions de mémoire qui sont spécifiées par les appelants.  
  
 [ICLRDataEnumMemoryRegionsCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Fournit une méthode de rappel pour que `EnumMemoryRegions` rapporte au débogueur le résultat d'une tentative d'énumération d'une région spécifiée de mémoire.  
  
 [ICLRDataTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Fournit des méthodes pour l'interaction avec un processus CLR cible.  
  
 [ICLRDataTarget2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Sous-classe de `ICLRDataTarget` qui est utilisée par la couche des services d'accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.  
  
 [Iclrdatatarget3, Interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Une sous-classe de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur l’exception.  
  
 [ICLRDebugging (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.  
  
 [ICLRDebuggingLibraryProvider (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 Inclut le [ProvideLibrary, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) méthode, qui obtient un fournisseur de bibliothèque interface de rappel qui permet de common language runtime des bibliothèques de débogage spécifiques à la version à la demande et le chargement.  
  
 [ICLRMetadataLocator (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Interface utilisée par la couche des services d'accès aux données pour localiser les métadonnées des assemblys dans un processus cible.  
  
 [ICorDebug (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l'environnement du CLR.  
  
 [ICorDebugAppDomain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Fournit des méthodes pour le débogage de domaines d'application.  
  
 [ICorDebugAppDomain2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Fournit des méthodes destinées au travail avec les tableaux, les pointeurs, les pointeurs fonction et les types ByRef. Cette interface est une extension de l'interface `ICorDebugAppDomain`.  
  
 [ICorDebugAppDomain3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Fournit des méthodes pour utiliser [!INCLUDE[wrt](../../../../includes/wrt-md.md)] dans un domaine d'application. Cette interface est une extension des interfaces `ICorDebugAppDomain` et `ICorDebugAppDomain2`.  
  
 [Icordebugappdomain4, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Étend logiquement le [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface à obtenir un objet managé à partir d’un wrapper CCW.  
  
 [ICorDebugAppDomainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Fournit une méthode qui retourne un nombre spécifié de valeurs `ICorDebugAppDomain` qui démarrent à l'emplacement suivant dans l'énumération.  
  
 [ICorDebugArrayValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Sous-classe de `ICorDebugHeapValue` qui représente un tableau unidimensionnel ou multidimensionnel.  
  
 [ICorDebugAssembly Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Représente un assembly.  
  
 [ICorDebugAssembly2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Représente un assembly. Cette interface est une extension de l'interface `ICorDebugAssembly`.  
  
 [Icordebugassembly3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Étend logiquement le [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface afin de fournir la prise en charge pour les assemblys conteneurs et les assemblys. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugAssemblyEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugAssembly`.  
  
 [ICorDebugBlockingObjectEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Fournit un énumérateur pour une liste de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.  
  
 [ICorDebugBoxValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Sous-classe de `ICorDebugHeapValue` qui représente un objet classe de valeur boxed.  
  
 [ICorDebugBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Représente un point d'arrêt dans une fonction ou un point de contrôle sur une valeur.  
  
 [ICorDebugBreakpointEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugBreakpoint`.  
  
 [ICorDebugChain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Représente un segment d'une pile des appels physique ou logique.  
  
 [ICorDebugChainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugChain`.  
  
 [ICorDebugClass Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugClass` représente le type générique non instancié.  
  
 [ICorDebugClass2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>. Cette interface étend `ICorDebugClass`.  
  
 [ICorDebugCode Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Représente un segment de code MSIL ou de code natif.  
  
 [ICorDebugCode2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Fournit des méthodes qui étendent les fonctions de `ICorDebugCode`.  
  
 [Icordebugcode3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Fournit une méthode qui étend [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) et [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) pour fournir des informations sur une valeur de retournée managée.  
  
 [Interface de ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Fournit une méthode qui permet à un débogueur énumérer les variables locales et les arguments dans une fonction.  
  
 [ICorDebugCodeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugCode`.  
  
 [ICorDebugComObjectValue (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Fournit des méthodes pour récupérer des objets d'interface mis en cache.  
  
 [ICorDebugContext Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Représente un objet de contexte. Cette interface n'a pas encore été implémentée.  
  
 [ICorDebugController Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.  
  
 [ICorDebugDataTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.  
  
 [Icordebugdatatarget2, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugdatatarget3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour fournir des informations sur les modules chargés. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugdebugevent, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Définit l'interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugEditAndContinueErrorInfo (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEditAndContinueSnapshot Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Sert d’interface de base abstraite pour déboguer des énumérateurs.  
  
 [ICorDebugErrorInfoEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEval Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.  
  
 [ICorDebugEval2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Étend `ICorDebugEval` pour offrir une prise en charge pour les types génériques.  
  
 [Icordebugexceptiondebugevent, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Étend la [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface pour prendre en charge les événements d’exception. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugExceptionObjectCallStackEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.  
  
 [ICorDebugExceptionObjectValue (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Étend la [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface pour fournir des informations de trace de pile à partir d’un objet d’exception managée.  
  
 [ICorDebugFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Représente un frame sur la pile en cours.  
  
 [ICorDebugFrameEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugFrame`.  
  
 [ICorDebugFunction Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Représente une fonction ou une méthode managée.  
  
 [ICorDebugFunction2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Étend logiquement `ICorDebugFunction` pour prendre en charge le débogage pas à pas pour « Uniquement mon code ».  
  
 [Icordebugfunction3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Étend logiquement le [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface pour fournir l’accès au code à partir d’une demande ReJIT.  
  
 [ICorDebugFunctionBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Étend `ICorDebugBreakpoint` pour prendre en charge les points d'arrêt au sein de fonctions.  
  
 [ICorDebugGCReferenceEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.  
  
 [ICorDebugGenericValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Sous-classe de `ICorDebugValue` qui s'applique à toutes les valeurs. Cette interface fournit les méthodes Get et Set pour la valeur.  
  
 [ICorDebugGuidToTypeEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Fournit un énumérateur pour un objet qui mappe les GUID et leurs objets `ICorDebugType` correspondants.  
  
 [ICorDebugHandleValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Sous-classe de `ICorDebugReferenceValue` qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.  
  
 [ICorDebugHeapEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Fournit un énumérateur pour les objets sur le tas managé.  
  
 [ICorDebugHeapSegmentEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Fournit un énumérateur pour les régions de mémoire du tas managé.  
  
 [ICorDebugHeapValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Sous-classe de `ICorDebugValue` qui représente un objet qui a été collecté par le garbage collector du CLR.  
  
 [ICorDebugHeapValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Extension de `ICorDebugHeapValue` qui fournit la prise en charge des handles d'exécution.  
  
 [ICorDebugHeapValue3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Expose les propriétés du verrou du moniteur d'objets.  
  
 [Icordebugilcode, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Représente un segment de code en langage intermédiaire.  
  
 [Icordebugilcode2, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Étend logiquement le [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface pour fournir des méthodes qui retournent le jeton de signature de variable locale d’une fonction et qui mappent le langage intermédiaire instrumenté d’un profileur (il Intermediate Language) aux offsets IL de méthode d’origine décalages.  
  
 [ICorDebugILFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 Représente un frame de pile de code MSIL.  
  
 [ICorDebugILFrame2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Extension logique de `ICorDebugILFrame`.  
  
 [Icordebugilframe3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 Fournit une méthode qui encapsule la valeur de retour d'une fonction.  
  
 [Icordebugilframe4, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire. Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
 [Icordebuginstancefieldsymbol, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Représente les informations sur les symboles de débogage pour un champ d’instance. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugInternalFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Identifie les types de frame pour le débogueur.  
  
 [ICorDebugInternalFrame2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Fournit des informations sur les frames internes, notamment l’adresse de la pile et la position par rapport à [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objets.  
  
 [Icordebugloadedmodule, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Fournit des informations sur un module chargé. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugManagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Fournit des méthodes pour traiter les rappels de débogueur.  
  
 [ICorDebugManagedCallback2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur. `ICorDebugManagedCallback2` est une extension logique de `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.  
  
 [ICorDebugMDA (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Représente un message d'Assistant Débogage managé (MDA).  
  
 [Icordebugmemorybuffer, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Représente une mémoire tampon en mémoire. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugmergedassemblyrecord, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Fournit des informations sur un assembly fusionné. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugMetaDataLocator (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Fournit des informations de métadonnées au débogueur.  
  
 [ICorDebugModule Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Représente un module CLR qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).  
  
 [ICorDebugModule2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Sert d'extension logique de `ICorDebugModule`.  
  
 [ICorDebugModule3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Crée un lecteur de symboles pour un module dynamique.  
  
 [ICorDebugModuleBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux modules spécifiques.  
  
 [Icordebugmoduledebugevent, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Étend la [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface pour prendre en charge les événements au niveau du module. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugModuleEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugModule`.  
  
 [Icordebugmutabledatatarget, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Étend la [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour prendre en charge des cibles de données mutables.  
  
 [ICorDebugNativeFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Implémentation spécialisée de `ICorDebugFrame` utilisée pour les frames natifs.  
  
 [ICorDebugNativeFrame2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Fournit des méthodes qui testent les relations entre frames enfant et parent.  
  
 [ICorDebugObjectEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux d'objets par leurs adresses virtuelles relatives.  
  
 [ICorDebugObjectValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Sous-classe de `ICorDebugValue` qui représente une valeur contenant un objet.  
  
 [ICorDebugObjectValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Étend `ICorDebugObjectValue` pour prendre en charge l'héritage et les substitutions.  
  
 [ICorDebugProcess Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Représente un processus qui exécute le code managé.  
  
 [ICorDebugProcess2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Extension logique de `ICorDebugProcess`.  
  
 [ICorDebugProcess3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Contrôle les notifications de débogueur personnalisées.  
  
 [Icordebugprocess5, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Étend la [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) local de l’interface pour prendre en charge l’accès au tas managé, pour fournir des informations sur le garbage collection d’objets gérés et pour déterminer si un débogueur charge des images à partir de l’application cache des images natives.  
  
 [Icordebugprocess6, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Étend logiquement le [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont codés dans les événements de débogage d’exception native et fractionnement de module virtuel. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugprocess7, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Fournit une méthode qui configure le débogueur afin de gérer les mises à jour des métadonnées en mémoire dans le processus cible.  
  
 [Icordebugprocess8, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Étend logiquement le [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface pour activer ou désactiver certains types de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rappels d’exception.  
  
 [ICorDebugProcessEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugProcess`.  
  
 [ICorDebugReferenceValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Sous-classe de `ICorDebugValue` qui prend en charge les types référence.  
  
 [ICorDebugRegisterSet (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Représente le jeu de registres disponible sur l'ordinateur qui exécute actuellement le code.  
  
 [ICorDebugRegisterSet2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Étend les fonctionnalités de `ICorDebugRegisterSet` pour les plateformes matérielles qui possèdent plus de 64 registres.  
  
 [ICorDebugRemote (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.  
  
 [ICorDebugRemoteTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 Fournit des méthodes qui vous permettent de déboguer les applications Silverlight dans l'environnement du CLR.  
  
 [ICorDebugRuntimeUnwindableFrame, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.  
  
 [ICorDebugStackWalk (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.  
  
 [Icordebugstaticfieldsymbol, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Représente les informations sur les symboles de débogage pour un champ static. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugStepper Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.  
  
 [ICorDebugStepper2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Prend en charge le débogage « Uniquement mon code ».  
  
 [ICorDebugStepperEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugStepper`.  
  
 [ICorDebugStringValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Sous-classe de `ICorDebugHeapValue` qui s'applique aux valeurs de chaîne.  
  
 [Icordebugsymbolprovider, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugsymbolprovider2, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Étend logiquement le [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface pour récupérer des informations sur les symboles de débogage supplémentaires. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugThread Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
 [ICorDebugThread2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Sert d'extension logique de `ICorDebugThread`.  
  
 [ICorDebugThread3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Fournit le point d’entrée pour le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) et les interfaces correspondantes.  
  
 [ICorDebugThread4 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 Fournit des informations sur le blocage des threads.  
  
 [ICorDebugThreadEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugThread`.  
  
 [ICorDebugType Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugType` représente le type générique instancié.  
  
 [Interface de ICorDebugType2](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Étend la [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface pour récupérer l’identificateur de type d’un type de base ou complexe (défini par l’utilisateur).  
  
 [ICorDebugTypeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugType`.  
  
 [ICorDebugUnmanagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 Fournit une notification des événements natifs qui ne sont pas mis directement en rapport avec le CLR.  
  
 « ICorDebugValue »  
 Représente une valeur de lecture ou d'écriture dans le processus en cours de débogage.  
  
 « ICorDebugValue2 »  
 Étend `ICorDebugValue` pour prendre en charge `ICorDebugType`.  
  
 [ICorDebugValue3 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour prendre en charge pour les tableaux supérieurs à 2 Go.  
  
 « ICorDebugValueBreakpoint »  
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux valeurs spécifiques.  
  
 « ICorDebugValueEnum »  
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugValue`.  
  
 [Interface de ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Représente une variable locale ou un argument d’une fonction.  
  
 [Interface de ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Fournit un énumérateur pour les variables locales et les arguments dans une fonction.  
  
 [Icordebugvariablesymbol, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Récupère les informations de symbole de débogage pour une variable. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugVirtualUnwinder (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Fournit des méthodes pour faciliter le déroulement de la pile. **Disponible sur .NET Native uniquement.**  
  
 [ICorPublish (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Sert d'interface générale pour les processus de publication.  
  
 [ICorPublishAppDomain (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Représente et fournit des informations à propos d'un domaine d'application.  
  
 [ICorPublishAppDomainEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Fournit des méthodes qui parcourent une collection d'objets `ICorPublishAppDomain` qui existent actuellement dans un processus.  
  
 [ICorPublishEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Sert comme base abstraite pour la publication des énumérateurs.  
  
 [ICorPublishProcess (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 Fournit des méthodes qui permettent d'accéder aux informations sur un processus.  
  
 [ICorPublishProcessEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Fournit des méthodes qui parcourent une collection d'objets `ICorPublishProcess`.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Débogage des Coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
