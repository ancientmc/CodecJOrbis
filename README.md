AncientMC's implementation of the CodecJOrbis plugin of the 3D Soundsystem, by Paul Lamb (paulscode.com), that ensures the
CodecMus class found in the Minecraft source works without messing with the vanilla code.

## Explanation ##
In early versions of Minecraft, the class CodecMus exists, containing this method:

```
    @Override
    protected openInputStream() throws IOException {
        return new MusInputStream(this, this.url, this.urlConnection.getInputStream());
    }
```

The version of CodecJOrbis compiled with the Minecraft jar contains this method in CodecJOrbis, hence the override. However,
upon doing research of multiple standalone versions of CodecJOrbis, I have not been able to find any version that contains this method.
When attempting to use these standalone versions in the past, either as maven implementations or something else, I've had to patch some things in 
into the vanilla code to ensure things work correctly as a result of not having the openInputStream() method. For the longest time I had assumed the in-jar version
of CodecJOrbis containing the openInputStream() method was a "vanilla" Paulscode version, but as far as I know that's not actually the case.

I can only conclude that Notch had implemented this method himself, into the CodecJOrbis class, to let him extend the class into CodecMus.

Instead of decompiling the class found within the MC jar, I've just manually added the method into this class. This version of CodecJOrbis
is the latest, dating back to November 23, 2010. 