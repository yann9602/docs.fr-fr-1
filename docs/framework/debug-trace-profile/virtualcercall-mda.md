---
title: "virtualCERCall MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), CER calls"
  - "virtualCERCall MDA"
  - "virtual CER calls"
  - "constrained execution regions"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# virtualCERCall MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `virtualCERCall` est activé comme un avertissement indiquant qu'un site d'appel dans un graphique des appels d'une région d'exécution limitée fait référence à une cible virtuelle, c'est\-à\-dire un appel virtuel à une méthode virtuelle non finale ou un appel à l'aide d'une interface.  Le Common Language Runtime \(CLR\) ne peut pas prédire la méthode de destination de ces appels uniquement à partir du langage intermédiaire et de l'analyse des métadonnées.  En conséquence, l'arborescence des appels ne peut pas être préparée dans le cadre du graphique d'une région d'exécution limitée et les abandons de threads dans ce sous\-arbre ne peuvent pas être bloqués automatiquement.  Cet Assistant Débogage managé vous avertit des cas où il peut s'avérer nécessaire d'étendre une région d'exécution limitée en utilisant des appels explicites à la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dès que les informations supplémentaires requises pour calculer la cible de l'appel sont connues au moment de l'exécution.  
  
## Symptômes  
 Des régions d'exécution limitée ne s'exécutent pas lors de l'abandon d'un thread ou du déchargement d'un domaine d'application.  
  
## Cause  
 Une région d'exécution limitée contient un appel à une méthode virtuelle qui ne peut pas être préparée automatiquement.  
  
## Résolution  
 Appelez <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> pour la méthode virtuelle.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)