---
title: 'Code Contracts &#8211; Part 1'
author: ammeep
layout: post
permalink: /2011/01/03/code-contracts-part-1/
dsq_thread_id:
  - 952312673
categories:
  - Code
tags:
  - Code
  - Code Contracts
image: http://placekitten.com/200/200
summary: hello and stuff
---
# 

Code Contracts are still reasonably hot off the press from Microsoft Research and its high time we get our heads around using them.

We all have written guard code at the tops of our method bodies. While often necessary, this quickly gets tiresome,repetitive and rather boring.

        public void SomeRandomMethod(string arg)
            {
                if (string.IsNullOrEmpty(arg))
                {
                    throw new ArgumentException("Saved by the bell");
                }
            }

Guard code such as this provides a way of preventing code from doing things which we do not expect, which is useful. However this approach has some limitations. We may do something later in the body of the method which would have thrown an unexpected exception, like trying to access the first char of a null string. Also when consuming a method with this kind of guard code, we may not find out we have done something stupid until our code executes and throws an exception.

Imagine a world where each time you called your method and violated a guard pre-condition (like passing null) defined in guard code you got a compilation warning, or error. You are imagining the world of Code Contracts. This new innovation brings a design by contract approach to .NET, allows static contract verification and even (conveniently) document generation.

How can you start living in such a world, I hear you ask. Well your first step is to install Code Contracts from the** [DevLabs][1] **site as they are not included as part of the visual studio install. The DevLabs install comes in two flavours, the premium and standard edition.

 [1]: http://msdn.microsoft.com/en-us/devlabs/dd491992.aspx

The premium download contains three tools** ccrewrite.exe, cccheck.exe and ccdoc.exe**. Runtime checking of contracts is generated by the ccrewrite tool, while cccheck is a static checker which verifies contracts at compile time. ccdoc is our document generator responsible for adding contract information to existing XML documentation.

Once installed (after a restart of Visual Studio) your project properties pages will have an extra tab “Code Contracts”. Now we can begin enjoying all the new goodies in the **[code contracts namespace][2]**  
![][3]

 [2]: http://msdn.microsoft.com/en-us/library/system.diagnostics.contracts.aspx
 [3]: https://lh4.googleusercontent.com/87yxH5G-SCHbeudn-Fnrk2OGdaSSdygCLfQApKqIEszbH14i5kGEr2WTPUG-_jIGsja_izho1vGOV8LFY_hpr4dh92W6jVfVav8RfWw_v4U_pfpqKw

That’s all on code contracts for now. Next up, I will show you how to configure code contracts for your project.