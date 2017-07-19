---
title: "How to: Map HRESULTs and Exceptions | Microsoft Docs"
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
  - "interoperation with unmanaged code, HRESULTs"
  - "exceptions, HRESULTs"
  - "interoperation with unmanaged code, exceptions"
  - "HRESULTs"
  - "COM interop, HRESULTs"
  - "COM interop, exceptions"
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Map HRESULTs and Exceptions
Les méthodes COM signalent les erreurs en retournant des valeurs HRESULT ; les méthodes .NET les signalent en levant des exceptions.  Le runtime gère la transition entre les deux.  Chaque classe d'exception dans le .NET Framework est mappée à une valeur HRESULT.  
  
 Les classes d'exceptions définies par l'utilisateur peuvent spécifier la valeur HRESULT appropriée.  Ces classes d'exceptions peuvent modifier dynamiquement la valeur HRESULT à retourner quand l'exception est générée par la définition du champ **HResult** sur l'objet exception.  Des informations supplémentaires relatives à l'exception sont fournies par le biais de l'interface **IErrorInfo**, qui est implémentée sur l'objet .NET dans le processus non managé.  
  
 Si vous créez une classe qui étend **System.Exception**, vous devez définir le champ HRESULT pendant la construction.  Sinon, la classe de base assigne la valeur HRESULT.  Vous pouvez mapper de nouvelles classes d'exceptions à un HRESULT existant en fournissant la valeur dans le constructeur de l'exception.  
  
 Notez que l'exécution ignorera parfois un `HRESULT` si le thread comporte un `IErrorInfo`.  Ce comportement peut se présenter si `HRESULT` et `IErrorInfo` ne représentent pas la même erreur.   ``  
  
### Pour créer une classe d'exception et la mapper à un HRESULT  
  
1.  Utilisez le code suivant pour créer une classe d'exception appelée `NoAccessException` et la mapper à `E_ACCESSDENIED` du HRESULT.  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;   
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 Vous pouvez rencontrer un programme \(écrit dans n'importe quel langage de programmation\) qui utilise à la fois un code managé et un code non managé en même temps.  Par exemple, le marshaleur personnalisé dans l'exemple de code suivant utilise la méthode **Marshal.ThrowExceptionForHR\(int HResult\)** pour lever une exception avec une valeur HRESULT spécifique.  La méthode consulte HRESULT et génère le type d'exception approprié.  Par exemple, dans le fragment de code suivant, HRESULT génère **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Le tableau suivant fournit le mappage complet à partir de chaque HRESULT vers sa classe d'exception comparable dans le .NET Framework.  
  
|HRESULT|Exception .NET|  
|-------------|--------------------|  
|**MSEE\_E\_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR\_E\_APPLICATION**|**ApplicationException**|  
|**COR\_E\_ARGUMENT ou E\_INVALIDARG**|**ArgumentException**|  
|**COR\_E\_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR\_E\_ARITHMETIC ou ERROR\_ARITHMETIC\_OVERFLOW**|**ArithmeticException**|  
|**COR\_E\_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR\_E\_BADIMAGEFORMAT ou ERROR\_BAD\_FORMAT**|**BadImageFormatException**|  
|**COR\_E\_COMEMULATE\_ERROR**|**COMEmulateException**|  
|**COR\_E\_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR\_E\_CORE**|**CoreException**|  
|**NTE\_FAIL**|**CryptographicException**|  
|**COR\_E\_DIRECTORYNOTFOUND ou ERROR\_PATH\_NOT\_FOUND**|**DirectoryNotFoundException**|  
|**COR\_E\_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR\_E\_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR\_E\_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR\_E\_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR\_E\_EXCEPTION**|**Exception**|  
|**COR\_E\_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR\_E\_FIELDACCESS**|**FieldAccessException**|  
|**COR\_E\_FILENOTFOUND ou ERROR\_FILE\_NOT\_FOUND**|**FileNotFoundException**|  
|**COR\_E\_FORMAT**|**FormatException**|  
|**COR\_E\_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR\_E\_INVALIDCAST ou E\_NOINTERFACE**|**InvalidCastException**|  
|**COR\_E\_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR\_E\_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR\_E\_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR\_E\_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR\_E\_IO**|**IOException**|  
|**COR\_E\_MEMBERACCESS**|**AccessException**|  
|**COR\_E\_METHODACCESS**|**MethodAccessException**|  
|**COR\_E\_MISSINGFIELD**|**MissingFieldException**|  
|**COR\_E\_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR\_E\_MISSINGMEMBER**|**MissingMemberException**|  
|**COR\_E\_MISSINGMETHOD**|**MissingMethodException**|  
|**COR\_E\_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR\_E\_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E\_NOTIMPL**|**NotImplementedException**|  
|**COR\_E\_NOTSUPPORTED**|**NotSupportedException**|  
|**COR\_E\_NULLREFERENCE ou E\_POINTER**|**NullReferenceException**|  
|**COR\_E\_OUTOFMEMORY ou**<br /><br /> **E\_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR\_E\_OVERFLOW**|**OverflowException**|  
|**COR\_E\_PATHTOOLONG ou ERROR\_FILENAME\_EXCED\_RANGE**|**PathTooLongException**|  
|**COR\_E\_RANK**|**RankException**|  
|**COR\_E\_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR\_E\_REMOTING**|**RemotingException**|  
|**COR\_E\_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR\_E\_SECURITY**|**SecurityException**|  
|**COR\_E\_SERIALIZATION**|**SerializationException**|  
|**COR\_E\_STACKOVERFLOW ou ERROR\_STACK\_OVERFLOW**|**StackOverflowException**|  
|**COR\_E\_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR\_E\_SYSTEM**|**SystemException**|  
|**COR\_E\_TARGET**|**TargetException**|  
|**COR\_E\_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR\_E\_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR\_E\_THREADABORTED**|**ThreadAbortException**|  
|**COR\_E\_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR\_E\_THREADSTATE**|**ThreadStateException**|  
|**COR\_E\_THREADSTOP**|**ThreadStopException**|  
|**COR\_E\_TYPELOAD**|**TypeLoadException**|  
|**COR\_E\_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR\_E\_VERIFICATION**|**VerificationException**|  
|**COR\_E\_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR\_E\_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Tous les autres HRESULT**|**COMException**|  
  
 Pour extraire des informations d'erreur étendues, le client managé doit examiner les champs de l'objet exception généré.  Pour que l'objet exception fournisse des informations utiles sur une erreur, l'objet COM doit implémenter l'interface **IErrorInfo**.  Le runtime utilise les informations fournies par **IErrorInfo** pour initialiser l'objet exception.  
  
 Si l'objet COM ne prend pas en charge **IErrorInfo**, le runtime initialise un objet exception avec les valeurs par défaut.  Le tableau suivant répertorie chaque champ associé à un objet exception et identifie la source des informations par défaut lorsque l'objet COM prend en charge **IErrorInfo**.  
  
 Notez que l'exécution ignorera parfois un `HRESULT` si le thread comporte un `IErrorInfo`.  Ce comportement peut se présenter si `HRESULT` et `IErrorInfo` ne représentent pas la même erreur.   ``  
  
|Champ d'exception|Source d'informations à partir de COM|  
|-----------------------|-------------------------------------------|  
|**ErrorCode**|HRESULT retourné à l'issue de l'appel.|  
|**HelpLink**|Si **IErrorInfo\-\>HelpContext** est différent de zéro, la chaîne est formée par la concaténation de **IErrorInfo\-\>GetHelpFile**, « \# » et **IErrorInfo\-\>GetHelpContext**.  Sinon, la chaîne est retournée à partir de **IErrorInfo\-\>GetHelpFile**.|  
|**InnerException**|Toujours une référence null \(**Nothing** en Visual Basic\).|  
|**Message**|Chaîne retournée à partir de **IErrorInfo\-\>GetDescription**.|  
|**Source**|Chaîne retournée à partir de **IErrorInfo\-\>GetSource**.|  
|**StackTrace**|Trace de la pile.|  
|**TargetSite**|Nom de la méthode ayant retourné le HRESULT qui a échoué.|  
  
 Les champs d'exception, tels que **Message**, **Source** et **StackTrace** ne sont pas disponibles pour **StackOverflowException**.  
  
## Voir aussi  
 [Advanced COM Interoperability](http://msdn.microsoft.com/fr-fr/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [Exceptions](../../../docs/standard/exceptions/index.md)