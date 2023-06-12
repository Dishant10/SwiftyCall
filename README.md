# SwiftyCall

SwiftyCall is an open-source networking library designed to make network requests a breeze for Swift developers. With SwiftyCall, you can easily integrate communication features into your Swift applications without getting caught up in complex networking code.

It's simple, swift and reliable. Forget about writing URLRequest, URLSession, JSONDecoder, Encoder and all of such terms, let SwiftyCall handle it all. 

# Installation
SwifyCall can be installed using Swift Package Manager. Xcode>File>Add Packages>https://github.com/Dishant10/SwiftyCall.git

SwiftyCall is openly and freely available at : https://github.com/Dishant10/SwiftyCall.git

# Usage

After adding SwiftyCall as a package to your project, simply import SwiftyCall.
After successfully importing the package, you can use the NetworkManager class which handles all the networking calls.
The fetch function takes the url of the API and the type of the JSON expected to decode as the function parameters.
To call the fetch function you need to use the shared instance of the NetworkManager class.
```swift
NetworkingManager.shared.fetch("https://backend-omega-seven.vercel.app/api/getjoke", type: [Joke].self)

```

Joke Type (struct)
```swift
struct Joke:Codable{
    let question:String
    let punchline:String
}
```

It is mandatory to provide the type of the JSON responsse. 
In the example, the Jokes API returns an array of Joke. Hence [Joke].self.

The function aslo has a compeletion handler closure which will be called with a Result<Type,Error> object where type is the type you have provided as the function argument and error if there's an error calling the API.

# To get jokes from the Jokes API (Example)

```swift
NetworkingManager.shared.fetch("https://backend-omega-seven.vercel.app/api/getjoke", type: [Joke].self) { res in
            switch res {
            case .success(let data):
                //                    print(data[0].question)
                //                    print(data[0].punchline)
                self.question = data[0].question
                self.punchline = data[0].punchline
            case .failure(let error):
                print(error)
            }
        }
```

# Examle App

To view SwiftyCall in its full form and in a real world application, go to this project repo - https://github.com/Dishant10/SwiftyCall-Example.git

This app uses the same jokes api used in to demonstrate the swiftycall usage and fully utilizes the power of SwiftyCall and you'll then agree how easy it to network in your app with SwifyCall.

# API used

https://backend-omega-seven.vercel.app/api/getjoke
