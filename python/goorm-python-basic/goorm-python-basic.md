# 무료 파이썬 기본편

[A basic python course](https://edu.goorm.io/learn/lecture/19917/무료-파이썬-기본편-6시간-뒤면-나도-개발자) from goormedu

---

## Standard Output

When using the print function, the distance between elements can be adjusted using `,` and `+`.

    print("Python", "Java")
    # Python Java

    print("Python" + "Java")
    # PythonJava

### `sep` parameter

Adding a `sep` parameter allows one to choose what comes in between elements. It *separates* the elements with the value of the parameter written.

    print("Python", "Java", sep=", ")
    # Python, Java

### `end` parameter

The `end` parameter chooses when to end the print function. The line ends when it matches with the value given.

    print("Python is fun.", end="?")
    print(" Don't you agree?")
    # Python is fun. Don't you agree?

### `sys.stdout`, `sys.stderr`


### `ljust`, `rjust`

As the meaning can be derived from the name, `ljust` means to adjust to the left, and `rjust` to the right.

    scores = {"math": 0, "english": 50, "science": 100}
    for subject, score in scores.items():
        print(subject.ljust(8), str(score).rjust(4), sep=":")
    # math    :   0
       english :  50
       science : 100

The number inside the method puts the values inside the length of the amount, and then adjusts it. 

### `zfill`

`zfill` secures the number of spaces given, and fills the empty spaces with 0.

    for num in range(1, 11):
        print(str(num).zfill(3))
    #  001
       002
       003
       004
       005
       006
       007
       008
       009
       010

### 