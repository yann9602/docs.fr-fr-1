---
title: "Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 071e0aa916e4b3464c7c0cbff6596cabc6b67906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="04497-102">Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04497-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="04497-103">Fournir des paramètres et retourner des valeurs dans une application multithread est complexe, car le constructeur de la classe thread doit recevoir une référence à une procédure qui n’accepte aucun argument et ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="04497-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="04497-104">Les sections suivantes présentent plusieurs moyens simples pour fournir des paramètres et retourner des valeurs à partir de procédures exécutées sur des threads distincts.</span><span class="sxs-lookup"><span data-stu-id="04497-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="04497-105">Fournir des paramètres pour des procédures multithread</span><span class="sxs-lookup"><span data-stu-id="04497-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="04497-106">Le meilleur moyen de fournir des paramètres pour un appel de méthode multithread consiste à inclure la méthode cible dans une classe et à définir les champs de cette classe à utiliser comme paramètres pour le nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="04497-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="04497-107">Cette approche présente l’avantage de vous permettre de créer une autre instance de la classe, avec ses propres paramètres, chaque fois que vous souhaitez démarrer un nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="04497-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="04497-108">Prenons l’exemple d’une fonction calculant la surface d’un triangle, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="04497-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="04497-109">Vous pouvez écrire une classe qui inclut la fonction `CalcArea` et crée des champs pour stocker les paramètres d’entrée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="04497-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="04497-110">Pour utiliser `AreaClass`, vous créez un objet `AreaClass`, puis vous définissez les propriétés `Base` et `Height` comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="04497-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 <span data-ttu-id="04497-111">Notez que la procédure `TestArea` ne vérifie pas la valeur du champ `Area` après avoir appelé la méthode `CalcArea`.</span><span class="sxs-lookup"><span data-stu-id="04497-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="04497-112">Étant donné que `CalcArea` s’exécute sur un thread distinct, le champ `Area` risque de ne pas être défini si vous le vérifiez immédiatement après avoir appelé `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="04497-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="04497-113">La section suivante présente une méthode plus appropriée pour retourner des valeurs à partir de procédures multithread.</span><span class="sxs-lookup"><span data-stu-id="04497-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="04497-114">Retourner des valeurs à partir de procédures multithread</span><span class="sxs-lookup"><span data-stu-id="04497-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="04497-115">Retourner des valeurs à partir de procédures exécutées sur des threads distincts est compliqué du fait que les procédures ne peuvent pas être des fonctions, ni utiliser d’arguments `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="04497-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="04497-116">Le moyen le plus simple de retourner des valeurs consiste à utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour gérer vos threads et déclencher un événement à la fin de la tâche, puis traiter les résultats à l’aide d’un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="04497-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="04497-117">L’exemple suivant retourne une valeur en déclenchant un événement à partir d’une procédure exécutée sur un thread distinct :</span><span class="sxs-lookup"><span data-stu-id="04497-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 <span data-ttu-id="04497-118">Vous pouvez fournir des paramètres et retourner des valeurs aux threads de Thread Pool en utilisant la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="04497-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="04497-119">Les threads de Timer Thread prennent également en charge un objet d’état à cet effet.</span><span class="sxs-lookup"><span data-stu-id="04497-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="04497-120">Pour plus d’informations sur le regroupement de threads et les composants Timer thread, consultez [le regroupement de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[le regroupement de threads](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) et [minuteries de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="04497-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04497-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04497-121">See Also</span></span>  
 [<span data-ttu-id="04497-122">Procédure pas à pas : multithreading avec le composant BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04497-122">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="04497-123">Regroupement des threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04497-123">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="04497-124">Synchronisation des threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04497-124">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="04497-125">Événements</span><span class="sxs-lookup"><span data-stu-id="04497-125">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="04497-126">Applications multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04497-126">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="04497-127">Délégués</span><span class="sxs-lookup"><span data-stu-id="04497-127">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="04497-128">Multithreading dans les composants</span><span class="sxs-lookup"><span data-stu-id="04497-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
