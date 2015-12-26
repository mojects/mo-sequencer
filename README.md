Function inside `sequencer` is parsed as a string.
All function calls prefixed with `/*A*/` are executed first, and then substituted by resulting value

    sequencer(function() {
    
        console.log('Square of 3', /*A*/someAsyncFunction(3).square);
        console.log('Just a line');
        console.log('Now square of 9', /*A*/someAsyncFunction(9).square);
        
    });
    
    
    function someAsyncFunction(number, done) {
        setTimeout(() => {
            done(null, { square: number * number });
        }, 100)
    }
