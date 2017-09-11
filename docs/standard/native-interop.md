---
title: "Interopérabilité native"
description: "Découvrez comment interagir avec les composants natifs dans .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: 9652986491f087b8fa175e2b4041063c71211178
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---

# <a name="native-interoperability"></a><span data-ttu-id="7e81f-104">Interopérabilité native</span><span class="sxs-lookup"><span data-stu-id="7e81f-104">Native Interoperability</span></span>

<span data-ttu-id="7e81f-105">Dans ce document, nous allons approfondir un peu les trois façons disponibles de faire de l’« interopérabilité native » à l’aide de .NET.</span><span class="sxs-lookup"><span data-stu-id="7e81f-105">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="7e81f-106">Voici quelques-unes des raisons qui peuvent vous inciter à appeler du code natif :</span><span class="sxs-lookup"><span data-stu-id="7e81f-106">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="7e81f-107">Les systèmes d’exploitation sont fournis avec un volume important d’API qui ne sont pas présentes dans les bibliothèques de classes managées.</span><span class="sxs-lookup"><span data-stu-id="7e81f-107">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="7e81f-108">Un bon exemple est l’accès à des fonctions de gestion de matériel ou de gestion de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7e81f-108">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="7e81f-109">La communication avec d’autres composants qui ont produit ou peuvent produire des ABI de style C (ABI natifs).</span><span class="sxs-lookup"><span data-stu-id="7e81f-109">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="7e81f-110">Cela concerne, par exemple, le code Java qui est exposé via l’[interface native Java (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou tout autre langage managé qui peut produire un composant natif.</span><span class="sxs-lookup"><span data-stu-id="7e81f-110">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="7e81f-111">Sur Windows, la plupart des logiciels qui sont installés, comme la suite Microsoft Office, inscrivent des composants COM qui représentent leurs programmes et permettent aux développeurs de les automatiser ou de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="7e81f-111">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="7e81f-112">Cela nécessite également l’interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="7e81f-112">This also requires native interoperability.</span></span>

<span data-ttu-id="7e81f-113">Bien entendu, la liste ci-dessus n’englobe pas toutes les situations et scénarios potentiels dans lesquels le développeur voudrait ou aurait besoin d’interagir avec des composants natifs.</span><span class="sxs-lookup"><span data-stu-id="7e81f-113">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="7e81f-114">La bibliothèque de classes .NET, par exemple, utilise la prise en charge de l’interopérabilité native pour implémenter un certain nombre de ses API, comme la prise en charge et la manipulation de la console, l’accès au système de fichiers, etc.</span><span class="sxs-lookup"><span data-stu-id="7e81f-114">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="7e81f-115">Notez, toutefois, qu’il existe une option, en cas de besoin.</span><span class="sxs-lookup"><span data-stu-id="7e81f-115">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="7e81f-116">La plupart des exemples de ce document sont présentés pour les trois plateformes prises en charge de .NET Core (Windows, Linux et Mac OS).</span><span class="sxs-lookup"><span data-stu-id="7e81f-116">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="7e81f-117">Toutefois, pour certains exemples courts et illustratifs, seuls des noms de fichiers et des extensions Windows sont cités (par exemple, « dll » pour les bibliothèques).</span><span class="sxs-lookup"><span data-stu-id="7e81f-117">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="7e81f-118">Cela ne signifie pas que ces fonctionnalités ne sont pas disponibles sur Linux ou Mac OS, cela a été décidé pour plus de commodité.</span><span class="sxs-lookup"><span data-stu-id="7e81f-118">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="7e81f-119">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="7e81f-119">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="7e81f-120">P/Invoke est une technologie qui vous permet d’accéder aux structures, aux rappels et aux fonctions des bibliothèques non managées à partir de votre code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-120">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="7e81f-121">Une grande partie de l’API P/Invoke est contenue dans deux espaces de noms : `System` et `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-121">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="7e81f-122">À l’aide de ces deux espaces de noms, vous pouvez accéder aux attributs qui décrivent la façon dont vous voulez communiquer avec le composant natif.</span><span class="sxs-lookup"><span data-stu-id="7e81f-122">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="7e81f-123">Commençons par l’exemple le plus courant, c’est-à-dire appeler des fonctions non managées dans votre code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-123">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="7e81f-124">Nous allons afficher une zone de message à partir d’une application de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="7e81f-124">Let’s show a message box from a command-line application:</span></span>

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="7e81f-125">L’exemple ci-dessus est relativement simple, mais il ne montre pas ce dont vous avez besoin pour appeler des fonctions non managées à partir de code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-125">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="7e81f-126">Examinons l’exemple :</span><span class="sxs-lookup"><span data-stu-id="7e81f-126">Let’s step through the example:</span></span>

*   <span data-ttu-id="7e81f-127">La ligne 1 montre l’instruction using de `System.Runtime.InteropServices`, qui est l’espace de noms qui contient tous les éléments dont nous avons besoin.</span><span class="sxs-lookup"><span data-stu-id="7e81f-127">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="7e81f-128">La ligne 5 introduit l’attribut `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-128">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="7e81f-129">Cet attribut est crucial, car il indique au runtime qu’il doit charger la DLL non managée.</span><span class="sxs-lookup"><span data-stu-id="7e81f-129">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="7e81f-130">Il s’agit de la DLL dans laquelle nous voulons effectuer des appels.</span><span class="sxs-lookup"><span data-stu-id="7e81f-130">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="7e81f-131">La ligne 6 est l’essentiel du travail de P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="7e81f-131">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="7e81f-132">Elle définit une méthode managée qui a **exactement la même signature** que la méthode non managée.</span><span class="sxs-lookup"><span data-stu-id="7e81f-132">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="7e81f-133">Notez que la déclaration a un nouveau mot clé, `extern`, qui indique au runtime qu’il s’agit d’une méthode externe et que, quand vous l’appelez, le runtime doit la trouver dans la DLL spécifiée dans l’attribut `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-133">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="7e81f-134">Le reste de l’exemple appelle simplement la méthode comme toute autre méthode managée.</span><span class="sxs-lookup"><span data-stu-id="7e81f-134">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="7e81f-135">L’exemple est similaire pour Mac OS.</span><span class="sxs-lookup"><span data-stu-id="7e81f-135">The sample is similar for macOS.</span></span> <span data-ttu-id="7e81f-136">La seule chose que vous devez modifier est, bien sûr, le nom de la bibliothèque dans l’attribut `DllImport`, car Mac OS a un schéma de nommage des bibliothèques dynamiques différent.</span><span class="sxs-lookup"><span data-stu-id="7e81f-136">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="7e81f-137">L’exemple ci-dessous utilise la fonction `getpid(2)` pour obtenir l’ID de processus de l’application et l’afficher dans la console.</span><span class="sxs-lookup"><span data-stu-id="7e81f-137">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

<span data-ttu-id="7e81f-138">Il est similaire sur Linux, bien sûr.</span><span class="sxs-lookup"><span data-stu-id="7e81f-138">It is similar on Linux, of course.</span></span> <span data-ttu-id="7e81f-139">Le nom de fonction est le même, car `getpid(2)` est un appel du système [POSIX](https://en.wikipedia.org/wiki/POSIX).</span><span class="sxs-lookup"><span data-stu-id="7e81f-139">The function name is same, since `getpid(2)` is [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="7e81f-140">Appel de code managé à partir de code non managé</span><span class="sxs-lookup"><span data-stu-id="7e81f-140">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="7e81f-141">Bien entendu, le runtime permet une communication fluide dans les deux sens, ce qui vous donne la possibilité d’effectuer des appels dans des artefacts managés à partir de fonctions natives, à l’aide de pointeurs de fonction.</span><span class="sxs-lookup"><span data-stu-id="7e81f-141">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="7e81f-142">Ce qui ressemble le plus à un pointeur de fonction dans le code managé est un **délégué**, c’est donc ce qui est utilisé pour autoriser les rappels du code natif dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-142">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="7e81f-143">La façon d’utiliser cette fonctionnalité est similaire au processus code managé vers code natif décrit plus haut.</span><span class="sxs-lookup"><span data-stu-id="7e81f-143">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="7e81f-144">Pour un rappel donné, vous définissez un délégué qui correspond à la signature et vous le passez dans la méthode externe.</span><span class="sxs-lookup"><span data-stu-id="7e81f-144">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="7e81f-145">Le runtime s’occupe du reste.</span><span class="sxs-lookup"><span data-stu-id="7e81f-145">The runtime will take care of everything else.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

<span data-ttu-id="7e81f-146">Avant de parcourir notre exemple, passons en revue les signatures des fonctions non managées dont nous avons besoin.</span><span class="sxs-lookup"><span data-stu-id="7e81f-146">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="7e81f-147">La fonction que nous voulons appeler pour énumérer toutes les fenêtres a la signature suivante : `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="7e81f-147">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="7e81f-148">Le premier paramètre est un rappel.</span><span class="sxs-lookup"><span data-stu-id="7e81f-148">The first parameter is a callback.</span></span> <span data-ttu-id="7e81f-149">Ce rappel a la signature suivante : `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="7e81f-149">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="7e81f-150">Maintenant, examinons l’exemple :</span><span class="sxs-lookup"><span data-stu-id="7e81f-150">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="7e81f-151">La ligne 8 dans l’exemple définit un délégué qui correspond à la signature du rappel dans le code non managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-151">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="7e81f-152">Notez la façon dont les types LPARAM et HWND sont représentés à l’aide de `IntPtr` dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-152">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="7e81f-153">Les lignes 10 et 11 introduisent la fonction `EnumWindows` de la bibliothèque user32.dll.</span><span class="sxs-lookup"><span data-stu-id="7e81f-153">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="7e81f-154">Les lignes 13 à 16 implémentent le délégué.</span><span class="sxs-lookup"><span data-stu-id="7e81f-154">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="7e81f-155">Dans cet exemple simple, nous voulons simplement générer le handle dans la console.</span><span class="sxs-lookup"><span data-stu-id="7e81f-155">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="7e81f-156">Enfin, dans la ligne 19, nous appelons la méthode externe et transmettons le délégué.</span><span class="sxs-lookup"><span data-stu-id="7e81f-156">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="7e81f-157">Les exemples de Linux et Mac OS sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7e81f-157">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="7e81f-158">Dans ces exemples, nous utilisons la fonction `ftw` qui se trouve dans `libc`, la bibliothèque C.</span><span class="sxs-lookup"><span data-stu-id="7e81f-158">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="7e81f-159">Cette fonction est utilisée pour parcourir des hiérarchies de répertoires et accepte un pointeur vers une fonction comme l’un de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="7e81f-159">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="7e81f-160">Cette fonction a la signature suivante : `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-160">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

<span data-ttu-id="7e81f-161">Un exemple Mac OS utilise la même fonction et la seule différence réside dans l’argument de l’attribut `DllImport`, car Mac OS conserve `libc` dans un emplacement différent.</span><span class="sxs-lookup"><span data-stu-id="7e81f-161">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

<span data-ttu-id="7e81f-162">Les deux exemples ci-dessus dépendent de paramètres et dans les deux cas, les paramètres sont fournis comme des types managés.</span><span class="sxs-lookup"><span data-stu-id="7e81f-162">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="7e81f-163">Le runtime prend « la bonne décision » et les traite dans leurs équivalents de l’autre côté.</span><span class="sxs-lookup"><span data-stu-id="7e81f-163">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="7e81f-164">Étant donné que ce processus est très important pour écrire du code interop natif de qualité, jetons un œil à ce qui se produit quand le runtime _marshale_ les types.</span><span class="sxs-lookup"><span data-stu-id="7e81f-164">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="7e81f-165">Marshaling de types</span><span class="sxs-lookup"><span data-stu-id="7e81f-165">Type marshalling</span></span>

<span data-ttu-id="7e81f-166">Le **marshaling** est le processus de transformation des types quand ils doivent franchir la limite entre code managé et code natif.</span><span class="sxs-lookup"><span data-stu-id="7e81f-166">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="7e81f-167">La raison pour laquelle le marshaling est nécessaire est que les types des codes managé et non managé sont différents.</span><span class="sxs-lookup"><span data-stu-id="7e81f-167">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="7e81f-168">Dans le code managé, par exemple, vous avez un élément `String`, tandis que dans le monde non managé, les chaînes peuvent être Unicode (« larges »), non-Unicode, terminées par Null, ASCII, etc. Par défaut, le sous-système P/Invoke tente de prendre la bonne décision en fonction du comportement par défaut que vous pouvez constater sur [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e81f-168">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span></span> <span data-ttu-id="7e81f-169">Toutefois, dans les cas où vous avez besoin de plus de contrôle, vous pouvez employer l’attribut `MarshalAs` pour spécifier le type attendu du côté du code non managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-169">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="7e81f-170">Par exemple, si nous voulons que la chaîne soit envoyée sous forme de chaîne ANSI terminée par Null, nous pouvons procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="7e81f-170">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="7e81f-171">Marshaling de classes et de structures</span><span class="sxs-lookup"><span data-stu-id="7e81f-171">Marshalling classes and structs</span></span>

<span data-ttu-id="7e81f-172">Un autre aspect du marshaling de types consiste à passer une structure à une méthode non managée.</span><span class="sxs-lookup"><span data-stu-id="7e81f-172">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="7e81f-173">Par exemple, certaines des méthodes non managées nécessitent une structure comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="7e81f-173">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="7e81f-174">Dans ce cas, nous devons créer une structure ou une classe correspondante dans la partie managée de l’environnement pour l’utiliser comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="7e81f-174">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="7e81f-175">Toutefois, cela ne suffit pas de définir la classe, nous devons aussi indiquer au marshaleur comment mapper des champs de la classe à la structure non managée.</span><span class="sxs-lookup"><span data-stu-id="7e81f-175">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="7e81f-176">C’est là qu’intervient l’attribut `StructLayout`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-176">This is where the `StructLayout` attribute comes into play.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="7e81f-177">L’exemple ci-dessus illustre de manière simple les appels dans la fonction `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="7e81f-177">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="7e81f-178">L’élément digne d’intérêt se trouve sur la ligne 4.</span><span class="sxs-lookup"><span data-stu-id="7e81f-178">The interesting bit is on line 4.</span></span> <span data-ttu-id="7e81f-179">L’attribut spécifie que les champs de la classe doivent être mappés séquentiellement à la structure de l’autre côté (non managé).</span><span class="sxs-lookup"><span data-stu-id="7e81f-179">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="7e81f-180">Cela signifie que le nom des champs n’a pas d’importance, seul leur ordre compte, car il doit correspondre à la structure non managée, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7e81f-180">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="7e81f-181">Nous avons déjà vu l’exemple correspondant sur Linux et Mac OS dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="7e81f-181">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="7e81f-182">Il est représenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7e81f-182">It is shown again below.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

<span data-ttu-id="7e81f-183">La classe `StatClass` représente une structure qui est retournée par l’appel du système `stat` sur les systèmes UNIX.</span><span class="sxs-lookup"><span data-stu-id="7e81f-183">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="7e81f-184">Elle représente les informations d’un fichier donné.</span><span class="sxs-lookup"><span data-stu-id="7e81f-184">It represents information about a given file.</span></span> <span data-ttu-id="7e81f-185">La classe ci-dessus est la représentation sous forme de structure stat dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="7e81f-185">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="7e81f-186">Là encore, les champs de la classe doivent être dans le même ordre que la structure native (vous pouvez les trouver en parcourant les pages man de votre implémentation UNIX préférée) et ils doivent avoir le même type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="7e81f-186">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="7e81f-187">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="7e81f-187">More resources</span></span>

*   <span data-ttu-id="7e81f-188">[Wiki PInvoke.net](http://www.pinvoke.net), un excellent Wiki avec des informations sur les API Win32 courantes et comment les appeler.</span><span class="sxs-lookup"><span data-stu-id="7e81f-188">[PInvoke.net wiki](http://www.pinvoke.net) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="7e81f-189">P/Invoke sur MSDN</span><span class="sxs-lookup"><span data-stu-id="7e81f-189">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="7e81f-190">Documentation Mono sur P/Invoke</span><span class="sxs-lookup"><span data-stu-id="7e81f-190">Mono documentation on P/Invoke</span></span>](http://www.mono-project.com/docs/advanced/pinvoke/)

