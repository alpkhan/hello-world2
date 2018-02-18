# Code Your Own Quiz

#easy questions and answers
easy_questions="May the 1 be with you.Do, or do not. There is no 2.So this is how liberty dies. With thunderous 3.I can feel your 4. It give you focus... makes you stronger.."
easy_answer=["force","try","applause","anger"]
#medium questions and answers
medium_questions="Aren't you a little short for a 1?.You must confront 2. Then, only then, a Jedi will you be. And confront him you will.There's always a bigger 3.Someday, I will become the most 4 Jedi ever."
medium_answer=["stormtrooper","Vader","fish","powerful"]
#hard questions and answers
hard_questions="1 your feelings, Lord Vader. You will know it to be true. He could destroy us.Always in motion is the 2.I'd just as soon kiss a 3.We seem to be made to 4. It's our lot in life."
hard_answer=["Search","future","wookie","suffer"]

blanks=["1","2","3","4"]

#Decides difficulty
def start_level():
    level=input("Please select a difficulty(easy, medium, hard):")
    if level=="easy":
        print ("Difficulty is",level)
        return level
    if level=="medium":
        print ("Difficulty is",level)
        return level
    if level=="hard":
        print ("Difficulty is",level)
        return level
    else:
        print("Wrong choise try again")
        return start_level()
    print ("Difficulty is",level)

#as seen in class
def word_in_pos(word, parts_of_speech):
    for pos in parts_of_speech:
        if pos in word:
            return pos
    return None

#as seen in class
def play_game(ml_string, parts_of_speech,user_input):    
    replaced = []
    ml_string = str(ml_string).split()
    for word in ml_string:
        replacement = word_in_pos(word, parts_of_speech)
        if replacement != None:
            word = word.replace(replacement, user_input)
            replaced.append(word)
        else:
            replaced.append(word)
    replaced = " ".join(replaced)
    return replaced



#get user inputs and check them according to difficulty

def control_asnwer(questions,answers):
    number_of_questions=0
    blank_no=1
    while blank_no<5:
        user_input=input("Please guess NO:"+str(blank_no)+" answer: \n")
        if user_input==answers[number_of_questions]:
            print ("!!!Correct!!! ")
            questions=play_game(questions,blanks[number_of_questions],user_input)
            print (questions)
            number_of_questions+=1
            blank_no+=1
        else:print("Wrong answer Please try again")
    return print("Congratulation You have completed Star Wars quiz")    

#main function for game
#decides difficulty of questions
def main_play():
    print("Welcome to Star Wars quiz")
    choose=start_level()
    if choose=="easy":
        print (easy_questions)
        control_asnwer(easy_questions,easy_answer)
    if choose=="medium":
        print (medium_questions)
        control_asnwer(medium_questions,medium_answer)
    if choose=="hard":
        print (hard_questions)
        control_asnwer(hard_questions,hard_answer)
main_play()

