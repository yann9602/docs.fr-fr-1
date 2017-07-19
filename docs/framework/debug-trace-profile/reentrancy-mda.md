---
title: "reentrancy MDA | Microsoft Docs"
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
  - "unmanaged code, debugging"
  - "transitioning threads unmanaged to managed code"
  - "reentrancy MDA"
  - "reentrancy without an orderly transition"
  - "managed debugging assistants (MDAs), reentrancy"
  - "illegal reentrancy"
  - "MDAs (managed debugging assistants), reentrancy"
  - "threading [.NET Framework], managed debugging assistants"
  - "managed code, debugging"
  - "native debugging, MDAs"
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# reentrancy MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `reentrancy` est activé lors d'une tentative de transition du code natif au code managé dans les cas où une commutation antérieure de code managé en code natif n'a pas fait l'objet d'une transition correcte.  
  
## Symptômes  
 Le tas d'objets est endommagé ou d'autres erreurs sérieuses se produisent lors de la transition du code natif au code managé.  
  
 Les threads qui commutent entre du code natif et du code managé dans un sens ou l'autre doivent exécuter une transition correcte.  Toutefois, certains points d'extensibilité de niveau inférieur dans le système d'exploitation, tels que le gestionnaire d'exceptions vectorisé, permettent de commuter entre du code managé et du code natif sans exécuter une transition méthodique.  Ces commutateurs sont sous le contrôle du système d'exploitation, plutôt que sous celui du Common Language Runtime \(CLR\).  Tout code natif qui s'exécute à l'intérieur de ces points d'extensibilité doit éviter d'exécuter des rappels dans le code managé.  
  
## Cause  
 Un point d'extensibilité du système d'exploitation de niveau inférieur, tel que le gestionnaire d'exceptions vectorisé, a été activé pendant l'exécution de code managé.  Le code d'application qui est appelé via ce point d'extensibilité tente d'effectuer un rappel dans le code managé.  
  
 Ce problème est toujours provoqué par le code d'application.  
  
## Résolution  
 Examinez la trace de la pile pour le thread qui a activé cet Assistant Débogage managé.  Le thread tente d'exécuter un appel illégal dans le code managé.  La trace de la pile doit révéler le code d'application utilisant ce point d'extensibilité, le code du système d'exploitation qui fournit ce point d'extensibilité et le code managé interrompu par le point d'extensibilité.  
  
 Par exemple, vous pourrez constater l'activation de l'Assistant Débogage managé activé lors d'une tentative d'appel au code managé à partir d'un gestionnaire d'exceptions vectorisé.  Sur la pile, vous verrez le code de gestion des exceptions du système d'exploitation et le code managé qui déclenche une exception telle que <xref:System.DivideByZeroException> ou <xref:System.AccessViolationException>.  
  
 Dans cet exemple, la méthode de résolution correcte consiste à implémenter complètement le gestionnaire d'exceptions vectorisé dans du code non managé.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
 L'Assistant Débogage managé signale une tentative de réentrance illégale.  Examinez la pile du thread pour en déterminer la raison et pouvoir résoudre le problème.  La sortie peut se présenter comme suit.  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant provoque la levée de <xref:System.AccessViolationException>.  Sur les versions de Windows qui prennent en charge la gestion des exceptions vectorisée, cela se traduit par l'appel au gestionnaire d'exceptions vectorisé managé.  Si l'Assistant Débogage managé `reentrancy` est activé, il s'activera pendant la tentative d'appel à `MyHandler` à partir du code de prise en charge de la gestion des exceptions vectorisée du système d'exploitation.  
  
```  
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## Voir aussi  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)