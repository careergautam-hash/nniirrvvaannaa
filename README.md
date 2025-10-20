class QuestionPaper:
    def __init__(self, coaching_name, exam_month, total_marks):
        self.coaching_name = coaching_name
        self.exam_month = exam_month
        self.total_marks = total_marks
        self.section_a = []
        self.section_b = []
        self.section_c = []

    def add_question(self, section, question):
        if section == "A":
            self.section_a.append(question)
        elif section == "B":
            self.section_b.append(question)
        elif section == "C":
            self.section_c.append(question)

    def generate_paper(self):
        print(f"{'=' * 50}")
        print(f"कोचिंग संस्थान: {self.coaching_name}")
        print(f"परीक्षा माह: {self.exam_month}")
        print(f"कुल अंक: {self.total_marks}")
        print(f"{'=' * 50}\n")

        print("खंड A: बहुविकल्पीय प्रश्न")
        print("निम्न में से किसी भी 50% प्रश्नों का उत्तर दें:\n")
        for i, question in enumerate(self.section_a, 1):
            print(f"{i}. {question}")

        print(f"\n{'-' * 50}\n")
        print("खंड B: संक्षिप्त उत्तर वाले प्रश्न")
        print("निम्न में से किसी भी 50% प्रश्नों का उत्तर दें:\n")
        for i, question in enumerate(self.section_b, 1):
            print(f"{i}. {question}")

        print(f"\n{'-' * 50}\n")
        print("खंड C: लंबे उत्तर वाले प्रश्न")
        print("निम्न में से किसी भी 50% प्रश्नों का उत्तर दें:\n")
        for i, question in enumerate(self.section_c, 1):
            print(f"{i}. {question}")
        print(f"{'=' * 50}")


# प्रश्न पत्र का प्रारंभ करें
qp = QuestionPaper(coaching_name="A K CLASSES", exam_month="दिसंबर 2025", total_marks=100)

# खंड A (बहुविकल्पीय प्रश्न) में प्रश्न जोड़ें
section_a_questions = [
    "अर्थ के विचार में संज्ञा के कितने प्रकार हैं?",
    "'सप्तर्षि' का सही संधि-विच्छेद क्या है?",
    "जो कम बोलता है उसे क्या कहते हैं?",
    "'संगम' शब्द का संधि-विच्छेद क्या है?",
    "लक्ष्मी के बड़े पुत्र का क्या नाम था?",
    "'महाभारत' क्या है?",
    "'आलोचना' का पर्यायवाची शब्द क्या है?",
    "'अभिमान' शब्द में कौन-सा उपसर्ग है?",
    "'बेईमान' में कौन-सा उपसर्ग है?",
    "'ज्ञानोदय' में कौन सी संधि है?"
]

# खंड B (संक्षिप्त उत्तर वाले प्रश्न) में प्रश्न जोड़ें
section_b_questions = [
    "'एक वृक्ष की हत्या' कविता में कवि शहर को किससे बचाने की बात करता है?",
    "कवि ने माली-मालिन किसे कहा है?",
    "सीमा, रजनी, आलो, शेफाली, आरती-पाँचों किसकी बहनें थीं?",
    "'भारत से हम क्या सीखें' क्या है?",
    "मिहिर भोज की ग्वालियर प्रशस्ति किस भाषा में है?",
    "'परंपरा का मूल्यांकन' निबंध किस लेखक की रचना है?",
    "गाँधीजी शिक्षा का उद्देश्य क्या मानते थे?",
    "घनानंद ने किस मार्ग को अत्यन्त सीधा व सरल कहा है?",
    "'रसखान' को किसने दीक्षा दी?",
    "'तुलनात्मक व्याकरण' किसकी रचना है?"
]

# खंड C (लंबे उत्तर वाले प्रश्न) में प्रश्न जोड़ें
section_c_questions = [
    "'अनामदास का पोथा' उपन्यास के लेखक कौन हैं?",
    "'मछली' कहानी में किस वर्ग का चित्रण है?",
    "'विद्यानुराग' में कौन सा समास है?",
    "'महादेवी वर्मा' की कौन सी कृति है?",
    "'अज्ञेय' का पूरा नाम क्या है?",
    "'ज्ञानपीठ पुरस्कार' किस कृति के लिए मिला था?",
    "गाँधीजी वकालत की पढ़ाई के लिए कहाँ गए थे?",
    "'साँस' शब्द का विशेषण क्या है?",
    "'उर्वशी' किसकी कृति है?",
    "मैक्समूलर ने किस देश को सर्वविध संपदा और प्राकृतिक सौंदर्य से परिपूर्ण माना है?"
]

# खंड A के लिए प्रश्न जोड़ें
for question in section_a_questions:
    qp.add_question("A", question)

# खंड B के लिए प्रश्न जोड़ें
for question in section_b_questions:
    qp.add_question("B", question)

# खंड C के लिए प्रश्न जोड़ें
for question in section_c_questions:
    qp.add_question("C", question)

# प्रश्न पत्र तैयार करें
qp.generate_paper()