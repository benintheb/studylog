# 무료 파이썬 기본편

[A basic python course](https://edu.goorm.io/learn/lecture/19917/무료-파이썬-기본편-6시간-뒤면-나도-개발자) from goormedu

---

## Standard Output

When using the print function, the distance between elements can be adjusted using `,` and `+`.

    print("Python", "Java")
    // Python Java

    print("Python" + "Java")
    // PythonJava

### `sep` parameter

Adding a `sep` parameter allows one to choose what comes in between elements. It *separates* the elements with the value of the parameter written.

    print("Python", "Java", sep=", ")
    // Python, Java

### `end` parameter

The `end` parameter chooses when to end the print function. The line ends when it matches with the value given.

    print("Python is fun.", end="?")
    print(" Don't you agree?")
    // Python is fun. Don't you agree?

### `sys.stdout`, `sys.stderr`


### `ljust`, `rjust`

As the meaning can be derived from the name, `ljust` means to adjust to the left, and `rjust` to the right.

    scores = {"math": 0, "english": 50, "science": 100}
    for subject, score in scores.items():
        print(subject.ljust(4), str(score).rjust(12), sep=":")