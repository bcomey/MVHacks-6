<template>
    <router-link to="/" id="Home">MVHS Logistic Map</router-link>
    <VButton x="80%" y="3%" width="120px" height="60px" text="About" fontSize="25px" styl="secondary" borderRadius="10px" @click = "goToAbout"></VButton>
    <VButton x="90%" y="3%" width="120px" height="60px" text="Map" fontSize="25px" styl="normal" borderRadius="10px"></VButton>
    <div id="HeaderSeparator"></div>
    <img id="Map" src="../assets/map2.png">
	<div id="BoxContainer">
		
		<MapBox v-for="mapbox in this.mapboxes" :x="mapbox.x" :y="mapbox.y" :width="mapbox.width" :height="mapbox.height" :text="mapbox.name" fontSize="8px" color="#c2ffd3" :on="mapbox.on" @click="displayInfo(mapbox.name)"></MapBox>
	</div>
	<div id="RightSeparator"></div>
    <div id="info"></div>
	
	<input v-on:keyup.enter="onEnter" />


	
  </template>
<script>
  import VButton from "./VButton.vue";
  import MapBox from "./MapBox.vue";
  import VInput from "./VInput.vue";
  export default {
      data(){
		return{
			view:"clubs",
			clubs:[
{
    "club_name" : "6th Man\n", 
    "category" : "Recreational\n", 
    "desc" : "6th man is a spirit based club that supports Mountain View sports. Members of 6th man attempt to boost school spirit and help sports teams feel supported and play better. 6th man brings the entire school together and builds a community that no other club can. \n", 
    "room" : "Monthly on Fridays at lunch in room 604\n",
    "room_number" : "604"
},
{
    "club_name" : "Algorithmic Programming Club\n", 
    "category" : "Academic\n", 
    "desc" : "The Competitive Programming CLub is a group whose members are interested in learning, practicing, and enhancing their skills in algorithmic programming. Our community event is participating in a coding competition called TeamsCode, where members can apply what they learn and practice. \n", 
    "room" : "Thursday Weekly in P5 during lunch\n",
    "room_number" : "P5"
},
{
    "club_name" : "Anatomy Club\n", 
    "category" : "Community Service and Academic\n", 
    "desc" : "The Anatomy Club is a group of students who will be exploring anatomy and physiology throughout the school year. Club meetings will consist of lectures to teach the systems to club members, these lectures will be made and taught by club executives who will use several resources such as textbooks and educational videos. We will also participate in other activities such as guest lectures, making models, and possible dissections.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 123\n",
    "room_number" : "123"
},
{
    "club_name" : "Animal Assisted Happiness\n", 
    "category" : "Community Service\n", 
    "desc" : "The Animal Assisted Happiness club is a group whose members are interested in working with the non-profit organization, Animal Assisted Happiness, to help bring smiles to kids with disabilities through the interaction with barnyard animals. Our club will raise money to use in projects to benefit the farm, help out when Animal Assisted Happniess comes to Mountain View High, travel to private visits at the farm with Mr. Q's class to assist the AAH staff, and work to recruit more students in the MVHS community to become volunteers for this incredible organization.\n", 
    "room" : "Bi Weekly on Wednesdays at lunch in room 708\n",
    "room_number" : "708"
},
{
    "club_name" : "Badminton Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The Badminton Club at Mountain View High School seeks to provide opportunities for team members and those who want to play badminton to meet and compete. For team members, this will give the opportunity to practice in the off-season and will also allow for new players interested in badminton to try out the sport. We will have mentors there to offer support and lessons for students to improve their skills. Since the club works closely with the school team, we will also fundraise to benefit the school team. As a club, we will be able to communicate with the general student body efficiently and connect students to our team community.\n", 
    "room" : "Fridays with variable frequency in the gym (due to booking concerns)\n",
    "room_number" : "Gym"
},
{
    "club_name" : "Biology Club\n", 
    "category" : "Academic\n", 
    "desc" : "The Biology Club is dedicated towards informing students about science related opportunities in the Bay Area, developing essential lab skills, and educating students about biology related careers and the many disciplines that the subject branches into. We will do this by participating in labs, bringing in guest speakers, and presenting informational slides during meetings.\n", 
    "room" : "Bi Weekly on Fridays at lunch in room 121\n",
    "room_number" : "121"
},
{
    "club_name" : "Black Student Union\n", 
    "category" : "Awareness and Cultural\n", 
    "desc" : "We created the Black Student Union Club as a means for black students to be more acknowledged, as well as a venue for everyone else to learn about the black community and our history, whether they are black or not. We intend on visiting the African American Museum in Oakland, for example, to have a deeper understanding of African American culture, history, and other topics. Not only that, but we'll be giving back to the black community in a variety of ways, including donating to the Black Lives Matter Movement and supporting local black businesses, among other things.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 720\n",
    "room_number" : "728"
},
{
    "club_name" : "Book Club\n", 
    "category" : "Academic and Recreational\n", 
    "desc" : "The Book Club is a group whose members enjoy reading, are interested in sharing and analyzing books, and wish to extend their passion for books to other people. Additionally, we will participate in book-related community service activities, such as book drives.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 113\n",
    "room_number" : "113"
},
{
    "club_name" : "Bring Change to Mind Club\n", 
    "category" : "Awareness\n", 
    "desc" : "Bring Change to Mind's High School Program gives teens a platform to share their voices and raise awareness around mental health. Our goal is to empower students to educate one another, and their comminities, and to create a culture of peer support within their schools. Togerther, we'll fight the stigma around mental illness. All club members get free access to Headspace to practice mindfulness!\n", 
    "room" : "Weekly on Mondays at lunch in room 703\n",
    "room_number" : "703"
},
{
    "club_name" : "Business Club (BEAM - Business, Entrepreneurship, and Math)\n", 
    "category" : "Academic\n", 
    "desc" : "BEAM is dedicated to promoting business among the MVHS student body by providing interactive talks from guest speakers and internships with local companies. Our goal is for our members to gain useful business experience to prepare them for the working world. Our community event would be an elevator pitch contest judged by guest speakers for all MVHS students to participate in. \n", 
    "room" : "Weekly on Tuesdays at lunch in room 720\n",
    "room_number" : "720"
},
{
    "club_name" : "ChangeZ\n", 
    "category" : "Awareness\n", 
    "desc" : "The ChangeZ Club recognizes the importance of student and youth voice when it comes to social activism. Our mission is to provide a platform for discussion amongst a wide variety of students who can start or continue a discourse around different social issues. Addtionally, our club strives to foster a culture of activism in the school community. \n", 
    "room" : "Weekly on Thursdays at lunch in 731\n",
    "room_number" : "731"
},
{
    "club_name" : "Chemistry Club\n", 
    "category" : "Academic\n", 
    "desc" : "The objective of the Chemistry Club is to provide practical knowledge and experience in chemistry outside of classrooms and further preparation for students in preparation for the USNCO, AP Chemistry exam, and other chemistry related exams in and out of school as well as providing exposure to areas of current research in chemistry. This will be achieved by providing students laboratory experience and lecutures from instructors in the field. \n", 
    "room" : "Weekly Thursday at Lunch in Room 120\n",
    "room_number" : "120"
},
{
    "club_name" : "Chess Club\n", 
    "category" : "Recreational\n", 
    "desc" : "Chess Club is a group of students who are interested in playing matches with other students recreationally each week. Players of all levels of experience are welcome, including students who are new to chess. Our members can choose to learn both the basics of chess and deeper tactics and strategies that improve the soundness and creativity of gameplay. Throughout the year, members will have the opportunity to participte in casual interschool tournaments on Lichess.org and in-person club tournaments. \n", 
    "room" : "Weekly on Tuesdays at lunch in room 725\n",
    "room_number" : "725"
},
{
    "club_name" : "Chinese Cultural Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The Chinese Cultural Club is a student orfanization striving to foster interest in or further connect with Chinese culture. Our goal is to promote the understanding of the many aspects of Chinese culture through food, games, nusic, arts and crafts, movies, and more.\n", 
    "room" : "Weekly in Room 513 at Lunch\n",
    "room_number" : "513"
},
{
    "club_name" : "Clinical Care for the Underserved Club (CCU)\n", 
    "category" : "Community Service\n", 
    "desc" : "The Clinical Care for the Underserved Club (CCU) is dedicated towards fundraising for the RotaCare Bay Area organization, a collection of local clinics that provide free healthcare services to homeless and low income individuals. These funds will subsidize the cost of medical examinations, diagnostic testing, lab testing, and medications for homeless and low income individuals.\n", 
    "room" : "Bi Weekly on Wednesdays at lunch in room 409\n",
    "room_number" : "409"
},
{
    "club_name" : "Computer Science Club\n", 
    "category" : "Academic, Competitive, and Recreational\n", 
    "desc" : "Our club intends to support students interested in computer science by engaging members in projects, lectures, and learning opportunities.\n", 
    "room" : "Weekly on Fridays at lunch in room 806\n",
    "room_number" : "806"
},
{
    "club_name" : "Computer Tinkering Club\n", 
    "category" : "Academic and Recreational\n", 
    "desc" : "The Computer Tinkering Club is a group whose members are interested in working with, maintaining, and building computers. Our members will be maintaining the computers in the Engineering lab, and will be learning about how to build, maintain, clean, and repair desktop computers as well. We may seek donations for older computers or use some of the older, unused computers in the school as well. Our community event is performing an education session to teach people about how to maintain, clean, and repair their desktop computers.\n", 
    "room" : "Weekly on Thursdays at lunch in room 802\n",
    "room_number" : "802"
},
{
    "club_name" : "ConnectUs Club\n", 
    "category" : "Academic and Cultural\n", 
    "desc" : "Our mission is to connect with Iwata Minami Ko to create a community and to safely and comfortably exchange modern culture.  We also strive to help students from other countries adapt to the English language.\n", 
    "room" : "Weekly at lunch on Thursdays\n",
    "room_number" : "?"
},
{
    "club_name" : "Creative Writing Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The Creative Writing Club is a group interested in writing, the humanities, improving and diversifying writing skills, providing assistance on papers/individual work, and working on a literary magazine. With contests and publication opportunities, as well as peer feedback, this club fosters a writing niche for students in a predominantly STEM-centered atmosphere, creating a space for casual or aspiring writers.\n", 
    "room" : "Weekly on Thursdays at lunch in room 102\n",
    "room_number" : "102"
},
{
    "club_name" : "Crypto Club\n", 
    "category" : "Academic\n", 
    "desc" : "The crypto Club is meant to introduce high school students to the new and emerging industries of blockchain and web3.0. Memebers will learn how to use and navigate this complex industry. We will mostly NOT trade real cryptocurrencies (we will use test-netwroks), as we are focused more on building rather than investing. Lessons on these topics will be taught to members, and members will work together to create innovative projects that benefit our community. \n", 
    "room" : "Monday's weekly @lunch in P5 \n",
    "room_number" : "P5"
},
{
    "club_name" : "Cubing Club\n", 
    "category" : "Competitive and Recreational\n", 
    "desc" : "The Cubing Club is a club where people learn how to solve puzzles such as the Rubik's Cube. It is also a place for experienced cubers to improve, learn new puzzles, and compete against each other. \n", 
    "room" : "Weekly on Tuesdays and Thursdays at lunch in room 419\n",
    "room_number" : "419"
},
{
    "club_name" : "Drama Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The Drama club seeks to connect MVHS students with a love of theatre by providing theatre games, events, and educational opportunities, One of our community events is the induction ceremony for the International Thespian Society (ITS), which is a celebration of MVHS theatre achievements for the year and an opportunity for students to join the esteemed International Thespian Society. \n", 
    "room" : "Weekly Thursdays at lunch in room 413\n",
    "room_number" : "413"
},
{
    "club_name" : "Drought Prevention Club\n", 
    "category" : "Community Service and Awareness\n", 
    "desc" : "The Drough Prevention Club is a group of motivated students who want to raise awareness of the effects of droughts and find creative ways to prevent droughts in California. We seek to create prototypes for potential devices that can be used to conserve water and knowledge of what can be done to prevent droughts. Our community event is presenting these devices and raising awareness of droughts to the public. \n", 
    "room" : "Bi Weekly on Wednesdays at lunch in room 513\n",
    "room_number" : "513"
},
{
    "club_name" : "Embrace Relief Club\n", 
    "category" : "Awarness, recreational\n", 
    "desc" : "MVHS embrace relief is a group whose members are dedicated to providing serivice to places & people in need. This club is a highschool chapter of embrace relief, a nonprofit organization which collabortaes with volunteers to deliver humanitarian aid & disaster relief to vulnerable communities around the world. Embrace relief focuses on hunger relief, education, womens empowerment, and other golbal topics. Our community event will be passing out fliers with an issue we want to raise awarness on\n", 
    "room" : "Monthly on Thrusdays at lunch in room 731\n",
    "room_number" : "731"
},
{
    "club_name" : "Entrepreneur Club\n", 
    "category" : "Academic\n", 
    "desc" : "The MVHS Entrepreneur Club is a community for aspiring entrepreneurs to start and develop their smal business or organization. We welcom entrepreneurs with all kinds of interests - selling artisan goods, making computer apps, helping the community with a nonprofit, you name it. Students can find partners, network, connect with mentors, share tips, and more! We also provide a great way for students to expand their reach through our community event, the MVHS small business fair. At this event, the MVHS community can learn about the amazing things students are building. Launch or grow your venture with the Entrepreneur Club!\n", 
    "room" : "Bi-Weekly on Fridays at lunch in Room 411\n",
    "room_number" : "411"
},
{
    "club_name" : "Fashion Art and Explorer Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The Fashion and Art Explorer Club focuses on ideas to communicate in creative ways. We want to gather incredible students who have diverse skills in different areas and are interested in fashion and art. MEmbers of our club willl explore and discuss the relationshio between fashion, art and the world around us from ancient to present, discovering the echo between former createors and us. Students will get precious experience and show our school spirits during the fasion show and exhibition which will newly present stduents ideas. Our purpose is to provide a platform for creatieve and unique students to express ideas and get effetive feedback for improvement.\n", 
    "room" : "Bi-Weekly on Wednesdays and Lunch in Room 110\n",
    "room_number" : "110"
},
{
    "club_name" : "Folklorico Club\n", 
    "category" : "Cultural\n", 
    "desc" : "MVHS is a group of students and educators interested in exploring our own culture through dance, and educating others on a significant part of our culture. Our goal is to enhance cultural experiences on campus by learning and teaching various cultural dances. We will seek donations and funding in order to obtain a range of costume, shoes and outfit accessories to be used during dance performances. \n", 
    "room" : "Thursday 2x a month at lunch\n",
    "room_number" : "?"
},
{
    "club_name" : "Foreign Linguistics Club\n", 
    "category" : "Academic, Cultural\n", 
    "desc" : "The foreign Linguistics club is a group whose members are intersted in the study of foreign languages and the Linguisitc makeup of those langauges. Our club hopes to foster an enviorment with support for a variety of different languages, namely those taught at MVHS (chinese, spanish, french, japanese). Naturally, no single person in the club will be able to support every language, but through your participation we will be able to practice and learn new langauges together! Events in the future may include: club sponsered cafe meetups, practice speaking, guest speakers, and other social gatherings\n", 
    "room" : "Weekly on wednesday @lunch\n",
    "room_number" : "?"
},
{
    "club_name" : "French Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The French Club is an organization whose members are devoted to studying and celebrating the French language and culture through group activities. Students of any skill level are able to join the French Club. \n", 
    "room" : "Weekly Thursdays at lunch in room 603\n",
    "room_number" : "603"
},
{
    "club_name" : "French Honors Society\n", 
    "category" : "Cultural and Academic\n", 
    "desc" : "The French Honors Society, or La Societe Honoraire de Francais, is a group whose members are devoted to studying the French Language and Culture. Members, all of whom participate in French 3H or above, are strong students who are interested in learning more about the culture and develiping speaking skills through group activities. \n", 
    "room" : "Weekly Friday at lunch in room 603\n",
    "room_number" : "603"
},
{
    "club_name" : "Game Development Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The Game Development Club is a group whose members are interested in games and how they are developed. Our members enjoy programming and designing games. Our community event is a Game Jam & Game Showcase, where club members cooperate to create games in a short amount of time, and we interact with the MVHS community in fun and memorable ways. \n", 
    "room" : "Weekly on Thursdays at lunch in room 801\n",
    "room_number" : "801"
},
{
    "club_name" : "Girls Who Code\n", 
    "category" : "Academic and Community Service\n", 
    "desc" : "The Girls Who Code club works to foster an environment in which women in technology at MVHS feel welcome and comfortable to develop their coding skills and to teach members of the community more about computer science through lessons in coding, professional visits and field trips, and attending fun events like hackathons. We work towards small-scale individual projects and group projects where club members develop their own websites and teach code at local middle schools.\n", 
    "room" : "Bi Weekly on Thursdays in room 806\n",
    "room_number" : "806"
},
{
    "club_name" : "Go Club\n", 
    "category" : "Cultural and Recreational\n", 
    "desc" : "MVHS Go Club is a caring community where we love to learn and play Go. We want to spread the joy of Go since it is mostly played in Asia. In the future we would love to host go tournaments to attract more go players and spread awareness of go.\n", 
    "room" : "Weekly on Fridays at lunch in room 602\n",
    "room_number" : "602"
},
{
    "club_name" : "Greenteam MVHS\n", 
    "category" : "Awareness and Community Service\n", 
    "desc" : "The Mountain View Green Team's goal on campus is to spread awareness around the environment. Through the projects we complete, we are aiming to push our school collectively and individuals personally to better the choices they make and thoroughly understand the consequences that they can have.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 117\n",
    "room_number" : "117"
},
{
    "club_name" : "GSA (Gender and Sexuality Alliance)\n", 
    "category" : "Awareness\n", 
    "desc" : "The GSA (Gender and Sexuality Alliance) Club is a group of students who are either members or allies of the LGBTQ+ community. Our  club serves as a safe space for queer youth, where they can be accepted for who they are and meet others like them. GSA also organizes LGBTQ+ activism and awareness events, to spread knowledge about the queer community to the wider population. \n", 
    "room" : "Weekly on Fridays at Lunch in Room 726\n",
    "room_number" : "726"
},
{
    "club_name" : "Happy Day Microfunds\n", 
    "category" : "Community Service and Awareness\n", 
    "desc" : "Happy Day Micro Fund is a community-involved club with the intent of fundraising money through club-organized events to provide support to striving entrepreneurs through loans, mentorships, and more. This club calls for motivated high school students who are willing to help give back to the less privileged members in our community, with a focus on minorities.\n", 
    "room" : "Weekly on Fridays at luncj in room 314\n",
    "room_number" : "314"
},
{
    "club_name" : "Helping P.A.W.S.\n", 
    "category" : "Awareness and Community Service\n", 
    "desc" : "Helping P.A.W.S is a group of dedicated students, whose members are interested in learning about the animals in our community and making a difference. Our goal is to research, discover, and execute new ways for students to raise awareness and make a positive difference in the lives of animals in our community. Our members will create new methods for the community to better care for all the animals in our area, both wild and domestic. Our community event will focus on spreading awareness about different important animal-related issues and providing methods for the community to help combat these problems.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 212\n",
    "room_number" : "212"
},
{
    "club_name" : "History Club\n", 
    "category" : "Academic\n", 
    "desc" : "The histroy club seeks to gather people with an interest in all fieslds of history for discussion and any knowledge histroical topics and current events chosen by either the officers or members. It will also hold study/reviews sessions in preperation for AP exams or large tests in hsiotry classes\n", 
    "room" : "3x/Month on thursdays @lunch in room 731\n",
    "room_number" : "731"
},
{
    "club_name" : "Homeless Action Club\n", 
    "category" : "Community Service and Awareness\n", 
    "desc" : "The purpose of the Homeless Action Club (HAC) is to provide food, toiletries, shelter, provisions for the homeless, particularly given the increasing number of homeless given the pandemic.  We will work with our community to solicit volunteers to participate in activities/projects such as collecting non-perishable, non-expired food, toiletries, etc.  We would work with institutions such as Hope\u2019s Corner in Mountain View, CA to deliver and/or serve breakfast, provide supplies for showers, support them in providing temporary shelter to the homeless.  We would increase awareness of the homelessness situation in our neighborhoods, cities, California, and our country, and brainstorm ways we as students can help.\n", 
    "room" : "Bi Weekly on Fridays at lunch in room 705\n",
    "room_number" : "705"
},
{
    "club_name" : "Ignition Club\n", 
    "category" : "Academic\n", 
    "desc" : "The Ignition Club is an accomplished club that competes, learns, and teaches at various events. Competitions include capture the flag (cybersecurity competition) and hackathons (24 hr product development,) where the club competes (often successfully) among other high schoolers as well as adults. Learning includes preparation for competitions, which includes research, coding, and UI design. Finally, we teach multiple sessions per month at CoderDojo, a worldwide nonprofit, racking up 100+ community service hours and leading the effort for curriculum reform for hundreds of students.\n", 
    "room" : "Weekly on Fridays at lunch in room 123\n",
    "room_number" : "123"
},
{
    "club_name" : "INARA Club\n", 
    "category" : "Community Service\n", 
    "desc" : "The INARA Club is a group of students dedicated to fundraising for INARA, an organization that provides medical aid to refugee children in the Middle East. Club members learn how to raise awareness about current humanitarian issues in the Middle East by participating in fundraisers and activities. Our community service events are operating tables at the Social Justice Fair and the Wellness Fair.\n", 
    "room" : "Bi Weekly on Fridays at lunch in room 729\n",
    "room_number" : "729"
},
{
    "club_name" : "Inventors Club\n", 
    "category" : "Academic and Recreational\n", 
    "desc" : "The Inventors Club strives to teach and promote engineering and the basics of robotics through fun and hands-on activities such as making simple remote-controlled robots, a trash-collecting robot as a part of community service by the end of the year, and teaching the basics of programming and computer science.\n", 
    "room" : "Bi Weekly Wednesdays at lunch in room 803\n",
    "room_number" : "803"
},
{
    "club_name" : "Japan Club\n", 
    "category" : "Cultural\n", 
    "desc" : "Japan Club is a group whose members are interested in a more in-depth study of Japanese culture, including music, Anime, video games, Cosplay, food, Origami, and so on. Japan Club is where students learn or share Japanese cultural activities.\n", 
    "room" : "Weekly on Thursdays at lunch in room 601\n",
    "room_number" : "601"
},
{
    "club_name" : "Japanese National Honor Society\n", 
    "category" : "Academic\n", 
    "desc" : "Celebrate & appreciate language, culture, & history. Members should be interested in expanding their japanese fluency & literacy.\n", 
    "room" : "Tuesdays Monthly @lunch in room 601\n",
    "room_number" : "601"
},
{
    "club_name" : "Jewish Student Union\n", 
    "category" : "Awareness\n", 
    "desc" : "The Jewish Student Union is a group whose members are interested in interacting and building a relationship and community with other Jewish students. We will do this through learning about the history and traditions of Israel, celebrating Jewish holidays, and participating in various events within the greater Bay Area Jewish community.\n", 
    "room" : "Bi Weekly On Mondays at lunch in room 728\n",
    "room_number" : "728"
},
{
    "club_name" : "K-pop Dance Club\n", 
    "category" : "Cultural\n", 
    "desc" : "kpop is a music genre from South Korea. This type of music is very popular in Asia, and has spread all over the world, including in the USA. Mountain View High School is a very diverse school filled with people from all over the world, and we have hundreds of clubs here, but my question is... \"Why don't we have a Kpop club?\" There are many students at MVHS who love Kpop. This club will allow other teenagers to listen, dance, and be exposed to what other teenagers across the world are listening, dancing, and being exposed to, establishing a connection with the culture that otherwise wouldn't have been made. We hope that our club will be as entertaining, fun, inviting, and mind opening as a k-pop club can be. Our community events will mostly consist of drives, canned food and clothing for those who need them. \n", 
    "room" : "Weekly on Thursdays at lunch in room P7\n",
    "room_number" : "P7"
},
{
    "club_name" : "Kapamilya Club\n", 
    "category" : "Community Service, Awareness, and Cultural\n", 
    "desc" : "The Kapamilya Club is a club of people who are interested in gaining a deeper understanding and connection with Filipino culture. Our goal is to spread the culture through fun activities. We aim to also spread awareness of tragedies that happen in the Philippines. Our community event is a showcase of the many different aspects of the Filipino culture (i.e., food, games, traditions). \n", 
    "room" : "Bi Weekly Wednesdays at lunch in room 731\n",
    "room_number" : "731"
},
{
    "club_name" : "Key Club\n", 
    "category" : "Community Service\n", 
    "desc" : "Mountain View Key Club is a club under Key Club International, the oldest and largest student-led organization which provides its members with opportunities to provide service, build character, and develop leadership. Our members perform a variety of service projects such as tree planting, making toys for shelter dogs, and organizing the MVHS Performing Arts Benefit Concert.\n", 
    "room" : "Weekly on Mondays at lunch in room 110\n",
    "room_number" : "110"
},
{
    "club_name" : "Korean Culture Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The Korean Culture Club is place where students can express and explore their interest in Korean culture/language and Korean history. Our members will seek to understand in depth of the culture and spread awareness and posituvuty of the culture with the MVHS community through participating in campus on campus community events and club meetings. \n", 
    "room" : "Tuesdays Bi-Weekly at Lunch in Rm 102\n",
    "room_number" : "102"
},
{
    "club_name" : "Latino Student Union\n", 
    "category" : "Cultural\n", 
    "desc" : "The Latino student union is a club whose purpose is to unify, inspire, educate, and advocate for latino culture. Our members promote Latino culture by participating in social, fundraiaing, and Cultural events within and outside of the MVHS Community. At the beginning of spanish heritage month, LSU will host a potluck to kick off the month-long celebrations.\n", 
    "room" : "Friday's weekly @lunch in rm 720\n",
    "room_number" : "720"
},
{
    "club_name" : "Latinx Tech Club\n", 
    "category" : "Academic\n", 
    "desc" : "The Latinx Tech Club is a group whose members are interested in learning introductory concepts related to programming and engineering. The club works to expose students of tradiontally underreprersented communities (i.e. Latinx) to the STEM field. This club serves as a pipline towards other existing program/courses that require experience and that have higher bar to entry. Our community event is helping run Week of Code at Mountain View High School.\n", 
    "room" : "Wednesday Weekly at Lunch in Room 806\n",
    "room_number" : "806"
},
{
    "club_name" : "Leo Club\n", 
    "category" : "Community Service\n", 
    "desc" : "The Leo Club is a philanthropy/community service club where students who enjoy volunteering can give back to their community. Students part of the Leo Club will have the opportunity to plan and participate in fun, diverse, and inclusive community service projects. We are also part of a parent organization, called the Lions Club, which is a non-profit organization dedicated to giving back through community service.\n", 
    "room" : "Bi Weekly on Thursdays in room 729\n",
    "room_number" : "729"
},
{
    "club_name" : "M1820\n", 
    "category" : "Awareness and Community Service\n", 
    "desc" : "M1820 exists to encourage Christians to boldly live out their faith on school grounds. It is our mission to disciple believers and equip them with wisdom and the Holy Spirit to make known the truth of Jesus Christ in the world starting with Mountain View High School. We seek to spread the Gospel, participate in community service projects, and engage in Biblical discussions in order to build our faith and share the hope that we have. \n", 
    "room" : "Weekly on Fridays at lunch in room 125\n",
    "room_number" : "125"
},
{
    "club_name" : "March For Our Lives\n", 
    "category" : "Awareness\n", 
    "desc" : "The March For Our Lives club is a club for students who are interested in activism and using their voice as students to fight for change to stop gun violence, in order to make MVHS and other schools around the nation a safer place. As a club, we will research and study episodes and trends of gun violence, lobby for legislation and policy change, and organise fundraisers.The goal of our club is to spread awareness and take action to this effect as students, by getting people to vote, pushing for legislative reform, spreading and promoting facts-based research, and raising money for communities in need.\n", 
    "room" : "Weekly on Mondays at lunch on zoom\n",
    "room_number" : "online"
},
{
    "club_name" : "Marine Biology and Ocean Conservation Club\n", 
    "category" : "Awareness, Academic, and Community Service\n", 
    "desc" : "The Marine Biology and Ocean Conservation Club is a dedicated group of individuals who are pasisonate in the field of Marine Biology and Ocean Conservation and wnat to help others pursue/explore their interest in this field . Our goal is to create an environment where anyone can be involved with ocean conservation and philanthropy through community service, volunteer projects, and awareness. \n", 
    "room" : "Bi weekly on wednesday @lunch in room 107 \n",
    "room_number" : "107"
},
{
    "club_name" : "Math Club\n", 
    "category" : "Academic, Competitive, and Community Service\n", 
    "desc" : "The Math Club focuses on competitive and proof-based math outside of the school framework. We prepare students to succeed at math competitions. We also teach the math team at Blach Middle School.\n", 
    "room" : "Weekly on Wednesdays at lunch\n",
    "room_number" : "?"
},
{
    "club_name" : "Math Mission Club\n", 
    "category" : "community service\n", 
    "desc" : "The math mission club is a club dedicated ti helping sutdents struggling in math, or students un underserved communities have access to sudficient math tutoring and help. Out members will have to pass a test to ensure that thye have an advanced undertsanding of alhgebra 1 material, and then they will be assigned to students in need of help for one hour of tutoring sessions every few weeks. Out community/service evebnt is to provide atleast 10 hours per member of free tutoring per semsester\n", 
    "room" : "Bi weekly on mondays @lunch in room 419\n",
    "room_number" : "419"
},
{
    "club_name" : "Mathematical Modeling Club\n", 
    "category" : "Competitive\n", 
    "desc" : "The mission of Mountain View High School's Math Modeling program is to educate students about math modeling and its applications to real world situations, as well as to provide them with the opportunity to compete in prestigious national math modeling competitions, where they can win prize money in scholarships. \n", 
    "room" : "Weekly on Wednesdays at lunch\n",
    "room_number" : "?"
},
{
    "club_name" : "Me Too MVHS\n", 
    "category" : "Awareness\n", 
    "desc" : "We advocate for sexual assault awaraness and improvement of sex education. Our goal is to create a safe space for those affected by sexual violence and be a group of allies.\n", 
    "room" : "Bi Weekly on Wednesdays at lunch in room TBD\n",
    "room_number" : "?"
},
{
    "club_name" : "Mock Trial Club\n", 
    "category" : "Academic and Competitive\n", 
    "desc" : "The Mock Trial Club aims to deliver an early exposure to the process of law and litigation through discussion of the law and its procedures as well as a year-long simulation of a trial that students participate in. They will compete against other schools and will be graded on performance and understanding of due process. Taught by attorney lawyers from Santa Clara\u2019s Public Defender\u2019s Office, students will have first-hand insight into how the system works and how to navigate its intense network of procedure.\n", 
    "room" : "Weekly on Tuesdays after school in the library\n",
    "room_number" : "library"
},
{
    "club_name" : "Music Outreach Club\n", 
    "category" : "Academic, Community Service\n", 
    "desc" : "The MVHS Music Outreach Club is a community that provides performance and community service opportunities to student musicians who have shown themselves to be capable, creative, and passionate. All instruments are welcome and will have the chance to perform in groups or individually at the MVHS Chamber Concert in the fall and spring, and time permitting, at senior homes, public spaces, and other venues as they wish. Students are able to share their love of music with each other, the school, and community through both socialization and volunteering.\n", 
    "room" : "Thursday, Biweekly in Packard Hall\n",
    "room_number" : "packard"
},
{
    "club_name" : "MVHS Bridge Club\n", 
    "category" : "Competitive\n", 
    "desc" : "The MVHS Bridge Club allows students who are interested in learning and playing bridge to come together and play matches/tournaments. Players of all levels are welcome, including students who are new to the game, and students with higher skill levels. Our members are able to decide whether to learn the basics or deeper tactics of bridge. Towards the end of the year, we will encourage all members to attend the Bay Area championship tournament, where schools from around the Bay Area come and compete for top awards. Throughout the school year, students will constantly play in tournament settings and practice to improve their skills. Community events include middle school teaching and playing bridge with seniors at a continuing care facility.\n", 
    "room" : "Weekly on Wednesdays at lunch in Room 106\n",
    "room_number" : "106"
},
{
    "club_name" : "MVHS Chapter of Junior State of America\n", 
    "category" : "Acadmic\n", 
    "desc" : "The mission of the Junior State of America Foundation (JSA) is to strengthen American democracy by educting and preparing high school students for lifelong involvement and responsibe leadership in a democratic society. JSA works to civically and politically engage students through debate, leadership development, and activism. Our community event will be a voter pre-registration drive and a thought talk, which is an open debate that operates under JSA activities guidelines.\n", 
    "room" : "Monthly on Mondays at lunch in room 102\n",
    "room_number" : "102"
},
{
    "club_name" : "MVHS Drama Llamas\n", 
    "category" : "Recreational\n", 
    "desc" : "Drama Llamas is a group with the intent of making all aspects of theatre available to everyone. We are committed to creating student-run theater and learning leadership skills. Whenever possible, we will perform student-written shows, and put on one full-scale musical at the end of the year, which will serve as our community event.     \n", 
    "room" : "Monday through Thursday Weekly starting after the Spartan Theatre Company spring musical\n",
    "room_number" : "theatre"
},
{
    "club_name" : "MVHS Dungeons and Dragons Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The MVHS Dungeons & Dragons club is a club in which members of the community who either know d&d or are eaer to learn the game engage in team bhuilding activities, imporv games, build confidence and community. We also teach new players the rules of dungeon and dragons, an interactive role-playing game ehich takes place in the midievel era inspired by the forgotten realms, and help organize and facilitate games. Our commnity even tis to volunteer at animal assisted happiness and help out with yard and farm work\n", 
    "room" : "Bi-weekly, Thursdays at Lunch in room 722\n",
    "room_number" : "722"
},
{
    "club_name" : "MVHS Medical Exploration Club\n", 
    "category" : "Community Service, Awareness, and Academic\n", 
    "desc" : "The MV Medical Exploration Club is a group for students to learn more about the field of medicine and healthcare. Club members will gain exposure to these careers through guest speakers and lectures about specific fields and health conditions. Additionally, students will get the opportunity to earn community service hours through fundraising and volunteering for medical related charities and organizations. \n", 
    "room" : "Bi Weekly on Thursdays at lunch in room 117\n",
    "room_number" : "117"
},
{
    "club_name" : "MVHS Spartonautics\n", 
    "category" : "None\n", 
    "desc" : "None\n", 
    "room" : "None\n",
    "room_number" : "?"
},
{
    "club_name" : "MVHS Spikeball Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The MVHS spikeball club is a group whose members are interested in learning, playimng, and competing in the game of roundnet. It also promotes a fun enviroment to not play the game with others but to also have fun and meet new people while doing so. \n", 
    "room" : "weekly on fridays @ lunch in room ??\n",
    "room_number" : "?"
},
{
    "club_name" : "National Art Honors Society\n", 
    "category" : "Community Service\n", 
    "desc" : "National Art Honor Society is community service through the means or art. We bring together the two disciplines for artists to use their skills and love for art to benefit the community. National Art Honor Society teaches student-led art classes for teachers, collaborates with clubs and cultural groups, and hosts activities for local elementary schools. \n", 
    "room" : "Weekly on Tuesdays at lunch in room 110\n",
    "room_number" : "110"
},
{
    "club_name" : "On Trend Collaborators Club\n", 
    "category" : "None\n", 
    "desc" : "The American Cancer Society On Trend Collaborators is a group whose members are interested in promoting the affordability and availability of sustainable fashion through volunteer work at the Discovery Shop in Los Altos affiliated with The American Cancer Society Discovery Shop. \n", 
    "room" : "None\n",
    "room_number" : "none"
},
{
    "club_name" : "Party Games Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The party games club is a group created with the purpose of giving students a place to have fun with their friends make new ones, and de-stress. Our community event will be a fundraiser\n", 
    "room" : "Wednesday Bi-weekly @ lunch in rm 511\n",
    "room_number" : "511"
},
{
    "club_name" : "Persian Culture Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The Persian Culture club strives to embrace and celebrate the beauty and uniqueness of persian culture and is a group of enthusiastic persian and non-persian MVHS students who are interested in learning more about Persian history and Persian culture through community activities and club meetings. Our community service event will be a persian culture table at lunch at school to teach our community about persian new year!\n", 
    "room" : "Bi Weekly on Wednesdays at lunch in the library\n",
    "room_number" : "library"
},
{
    "club_name" : "Physics and Astronomy club\n", 
    "category" : "Academic\n", 
    "desc" : "MVHS Physics and Astronomy Club is a commmunity of students interested in the subject of physics, astronomy, and astrophysics. The Club is dedicated to providing practical curriculum, competition preperation, coursework assistance, and fun leisure activities, pertaining to physics, and sciences.\n", 
    "room" : "Weekly on Fridays at lunch in 617\n",
    "room_number" : "617"
},
{
    "club_name" : "Programming for Data Science Club (PDSC)\n", 
    "category" : "Competitive and Academic\n", 
    "desc" : "The Programming for Data Science Club teaches student technical and non-technical skills involved in data science. Students will acquire fundamental data analytical skills relatied to statistical modeling through hands-on analysis of real-world datasets such as economic data, health data, geographical data, and social networks. Club members will explore machine learning algorithims, statistical inference, data wrangling, and data visualization. They will learn programming languages (Python and R) and platforms (Google Collab) used for data analysis, workflows, and research. Students will also learn about the ethics side of data science and how it can (and will) impact people in the real world. Our weekly meetings will involve lessons covering these topics as well as workshops for building predictive models to participate in competitions.\n", 
    "room" : "Weekly on Tuesdays at lunch in room 106\n",
    "room_number" : "106"
},
{
    "club_name" : "Psych Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The PYSCH Club seeks to help its members become more well rounded and successful when living on their own. It seeks to give members practical skills everyone should know, but that are not necessarily taught in school or at home. \n", 
    "room" : "Wednesday Weekly at Lunch in Room 706\n",
    "room_number" : "706"
},
{
    "club_name" : "Random Acts of Kindness\n", 
    "category" : "Community Service and Recreational\n", 
    "desc" : "The Random Acts of Kindness Club is dedicated to providing spontaneous and small acts of kindness in the MVHS school community. Our members design and assemble small gifts or messages to spread to peers throughout their school community in order to create a more positive environment on campus. Our club aims to interact with the community further through fundraising, with events including restaurant partnerships and bake sales. \n", 
    "room" : "Bi Weekly on Wednesdays at lunch in room 731\n",
    "room_number" : "731"
},
{
    "club_name" : "Red Cross Club\n", 
    "category" : "Community Service\n", 
    "desc" : "Red Cross Club\u2019s purpose is to better our community by providing opportunities to local teens to volunteer through their local red cross chapter as well as giving them leadership experience through setting up their own fundraisers and volunteer events.\n", 
    "room" : "Bi Weekly on Fridays at lunch in room 110\n",
    "room_number" : "110"
},
{
    "club_name" : "Russian Club\n", 
    "category" : "Cultural\n", 
    "desc" : "The Russian Club is a group whose members, Russian or not, are interested in embracing Russian culture. This includes celebrating Russian traditionas and going to local Russian events. Anyone interested in expanding their knowledge of Russian history, culture, and language is welcome to join!\n", 
    "room" : "Monthly on Wednesdays at lunch in room 112\n",
    "room_number" : "112"
},
{
    "club_name" : "Sailing Club\n", 
    "category" : "Competative\n", 
    "desc" : "The Sailing Club is a club for anyone interested in sailing and learning more about the sport. As our club is designed for sailors of verying skill levels, including no prior experience, more experienced members will instruct less experienced sailors in order to allow everyone to gain new skills. We will host community events where club members will get on-the-water siling practice in addition to the classroom knowledge they gain in school\n", 
    "room" : "Wednesdays weekly @lunch in P5\n",
    "room_number" : "P5"
},
{
    "club_name" : "Science Olympiad\n", 
    "category" : "Competitive and Academic\n", 
    "desc" : "The MVHS Science Olympiad club educates and inspires students in all STEM (science, technology, engineering, and math) disciplines through hands-on activities. The club includes team members that compete at various Science Olympiad competitions, and also provides learning opportunities to explore science further. During workshop meetings we do lab activities, have subject expert lectures, and prepare for upcoming competitions.\n", 
    "room" : "Monthly on Tuesdays at lunch in room 617\n",
    "room_number" : "617"
},
{
    "club_name" : "SLAM Magazine\n", 
    "category" : "Academic\n", 
    "desc" : "SLAM Magazine is an organization and publication that is dedicated to illuminating social justice issues in our community that don't receive mainstream attention. We strive to amplify unheard voices and provide insight and nuance into the gears of systems of oppression based on race, ethnicity, gender, ability, and other identities through the arts. For our team members, our organization provides career-applicable skills and experience in design, photography, media marketing, business, and writing or journalism. Students work with their teams and as an organization to produce two issues each year that get sold and distributed throughout the MVLA community.\n", 
    "room" : "Weekly on Wednesdays after school in room 109\n",
    "room_number" : "109"
},
{
    "club_name" : "South Asian Student Union\n", 
    "category" : "Cultural\n", 
    "desc" : "The South Asian Student Union is a club where members will learn about South Asian Heritage, traditions, modern adaptations/stereotypes of India and also share their experiences at South Asians in America. Our club hopes to unite the South Asian Community in Mountain View High School and to build self pride and confidence in their race.\n", 
    "room" : "Weekly on Thursdays at lunch in room 725\n",
    "room_number" : "725"
},
{
    "club_name" : "Spartan Buddies Club\n", 
    "category" : "Awareness\n", 
    "desc" : "We are a club that strives to build friendships between mainstream students with(our buddies)and without disabilities. We believe no matter what abilities you have, everyone deserves a friend. We hope to create a more inclusive environment at MVHS through friendships. \n", 
    "room" : "Weekly on Thuesdays at lunch in room 708\n",
    "room_number" : "708"
},
{
    "club_name" : "Spartan Dance Club\n", 
    "category" : "Recreational\n", 
    "desc" : "Spartan Dance Club is a group whose members range from all types of backgrounds and levels of experience but come together as one to enjoy dance. Our goal is to spread positivity and joy through our passion for dance, and spread those feelings to our community audiences. Community events include dancing for Mountain View senior citizens at the senior center, performing in school rallies or at community events such as the Mountain View Tree Lighting, and performing and encouraging runners at the San Jose Turkey Trot. \n", 
    "room" : "Weekly on Wednesdays after school in room P7\n",
    "room_number" : "P7"
},
{
    "club_name" : "Spartan Robotics\n", 
    "category" : "Academic, Competitive, Community Service, and Recreational\n", 
    "desc" : "Achieve Anything, Break Boundaries, Create Communities\n", 
    "room" : "Weekly on Wednesdays in room New Engineering Complex\n",
    "room_number" : "805"
},
{
    "club_name" : "Speech and Debate\n", 
    "category" : "Competitive and Academic\n", 
    "desc" : "At MVLASD, we believe Speech and Debate (also known as \"forensics\") is one of the most valuable activities a student can participate in. Participants develop research skills, strategies that will help them on standardized tests, and the ability to speak in front of large groups with poise and confidence. Students also see dramatic improvements in writing organization, clarity and concision of speech and prose, and the ability to think quickly, critically, and from multiple perspectives. Students learn to set goals, delineate the steps needed to achieve them, and then hit the ground running! Students make lifelong friends in speech and debate! High school is a critical period for developing social connections, and forensics students often say speech and debate feels like a second home to them. Please check out our website: mvlasd.club for more information.\n", 
    "room" : "After school in the library\n",
    "room_number" : "library"
},
{
    "club_name" : "STEAM\n", 
    "category" : "Community Service\n", 
    "desc" : "The STEAM Club is a youth led organization whose goal is to bring opportunities and resources to the children of underprivileged communities in the Bay Area by teaching elementary school students STEM and art twice a month. \n", 
    "room" : "Bi Weekly on Mondays at lunch in room 121\n",
    "room_number" : "121"
},
{
    "club_name" : "STEM Research Pioneers\n", 
    "category" : "Academic\n", 
    "desc" : "STEM Research Pioneers is a club that approaches striving MVHS students who are seeking research opportunities related to the STEM field. Specifically, the club aims to provide advanced research techniques and insights, and offer an online platform that showcases the publications of student research on an extensive scale. In addition, the club is a place where students passionate for research can collaboratively share their ideas and be involved in a tight-knit community of like-minded students who can work together to learn, explore, and grow in the fields of STEM. In the long term, the club can participate in research competitions like ISEF and also hold community presentations at MVHS. Separate from research opportunities and publications, the club invites guest speakers and professionals in respective fields to provide mentorship/insight on the topics of interest.\n", 
    "room" : "Weekly on Thursdays at lunch in room 121\n",
    "room_number" : "121"
},
{
    "club_name" : "Sunrise Club\n", 
    "category" : "Awarness\n", 
    "desc" : "The sunrise club is our local school chapter of the national sunrise movement. Our goal is to combat climate chnage through advocacy, education, and action. We aim to be leaders in our community and advocate for what we believe in by taking charge to create the chnage we want to see, both regarding the neviorment aas well as othe rimportnat issues, such as the global pandemic. \n", 
    "room" : "Tuesdays Monthly @lunch in room 212\n",
    "room_number" : "212"
},
{
    "club_name" : "UNICEF\n", 
    "category" : "Awareness\n", 
    "desc" : "Through a partnership with UNICEF International, our club works to defend the rights and save the lives of children across the globe. We do this through a variety of fundraiser events, including on-campus events and partnerships with other organizations.\n", 
    "room" : "Bi Weekly at lunch in room P1\n",
    "room_number" : "P1"
},
{
    "club_name" : "Unidos\n", 
    "category" : "Community Service\n", 
    "desc" : "The UNIDOS club tutors at local schools through partnering with the Beyond the Bell and CollegeBound after school programs. Beyond tutoring, we aim to provide elementary and middle school students with mentors that will share their experiences as students and community members and instill in the younger students the importance of academic dedication and positive values.\n", 
    "room" : "Monthly on Mondays after school in room 611\n",
    "room_number" : "611"
},
{
    "club_name" : "Video Production Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The Video Production club is a group of people who are passionate about video production, but don\u2019t have the finest skills or equipment, but we try to improve together and learn together. We will invite people to come watch our videos as a mini video production club \u201cfilm festival\u201d twice a year.  \n", 
    "room" : "Weekly on Mondays at lunch in room 404\n",
    "room_number" : "404"
},
{
    "club_name" : "Weight-Lifting Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The weight-lifting club is a group whose members will learn all about the sport/hobby of weight-ligting. Our members will be able to apply the knowledge we give them inside the gym. Our community event will be a group session at The City Sports off of grant road. \n", 
    "room" : "Monthly, Friday at Lunch in Rm 409\n",
    "room_number" : "409"
},
{
    "club_name" : "Wellness Club\n", 
    "category" : "Recreational\n", 
    "desc" : "The wellness club provides a safe, positive space to students who need to de-stress during the school day. We plan to have coloring pages, games, and stress toys thats students can use druing lunch to destress and get their mind off of their test next period. \n", 
    "room" : "Monday's Weekly @lunch in rm 702 \n",
    "room_number" : "702"
},
{
    "club_name" : "Women in STEM\n", 
    "category" : "Community Service and Competitive\n", 
    "desc" : "The Women in STEM club is a group whose members are interested in conducting research and using technology to solve real-world problems. We foster STEM learning through participating in women-oriented competitions such as the SWENext Club Challenge, the Toshiba Exploravision, and the MIT Think presentation. We are planning to build a model and analytics using data to solve environmental issues. \n", 
    "room" : "Bi Weekly on Tuesdays at lunch in room 617\n",
    "room_number" : "617"
},
{
    "club_name" : "Women's Empowerment Club\n", 
    "category" : "Community Service, Awareness \n", 
    "desc" : "The goal of the Women's Empowerment club is to advocate for gender equality on a school-wide, community, and global basis. Through our participation in several service projects throughout the year as well as empowerment workshops, we hope to create a welcoming and safe space while making a positive impact in our community.\n", 
    "room" : "Monthly on Tuesday at Lunch in Room 102\n",
    "room_number" : "102"
},
{
    "club_name" : "Taiwanese Student Union\n", 
    "category" : "Cultural\n", 
    "desc" : "The Taiwanese Student Union (TSU) aims to build a safe and inclusive enviorment at Mountain View High School where memebers are able to share their cultural experiences in Taiwan. This club will educate students on a culture not often talked about. This club will educate students on a culture not often talked about. The taiwanese student Union will also benefit each member's communication and speaking skills. Some topics we will cover include local attractions, different cities, and taiwanese food. \n", 
    "room" : "Bi-weekly on friday's  at lunch in room ?\n",
    "room_number" : "?"
},
{
    "club_name" : "Clay club\n", 
    "category" : "Recreational\n", 
    "desc" : "Clay Club will offer an artictic enviorment to make ceramic art and build creative community. Our community event will show our MVHS community ceramic art in public displays and events will focus on raising funds and sharing the ceramics experiences with students and staff. \n", 
    "room" : "Monthly on thrusdays in room 111\n",
    "room_number" : "111"
},
{
    "club_name" : "Feminism & Philosophy in Media\n", 
    "category" : "Awarnness, Academic, Cultural\n", 
    "desc" : "The Feminism and Philosophy in Media (FPM) is a club whose memebers are interested in how traditional patriarchal philosophy intereacts with the narratives of women to influence modern-day media. As a club, we will delve depper into how feminist media both unconciously and consiously reflects the ideals of various influential philosophers. In addition, we will learn about the lives of feminist and female philosophers - both past and present - who have worked to combat the foundations that the patriarchy is built on, as well as construct complex ideas of our own.\n", 
    "room" : "Monday's Weekly @lunch in rm 702 \n",
    "room_number" : "702"
},
{
    "club_name" : "Information Security Club\n", 
    "category" : "Competative, Recreational\n", 
    "desc" : "The informational security club is dedicated to educating students about various aspects of offensive and defensive information security. Our community project is the contribution of code to make free and open source software even better, and contribution of writeups/tutorials online to assist beginning information security students.\n", 
    "room" : "Tuesdays Weekly @lunch in rm 513 \n",
    "room_number" : "513"
},
{
    "club_name" : "Geography Club\n", 
    "category" : "Academic\n", 
    "desc" : "The purpose of geography club is to educate those who are interested in the vast locations of our world, as well as the cultures, histroy, and other facts about those places. We will presesnt enticing lectures and games tou our members, as well as give them the opportunity to lead those activites.\n", 
    "room" : "Tuesdays Bi-weekly @lunch in rm 722\n",
    "room_number" : "722"
},
{
    "club_name" : "Photography Club\n", 
    "category" : "None\n", 
    "desc" : "The photography club is a recreational clu whose mission is to supply a photography club to students who can not accomidate another period in their schedules in and out of school. Photography club is a safe space where students with similar interest can learn how to take and edit pictures while hangingn out with friends and playing recreational games.\n", 
    "room" : "Tuesday @lunch in rm 104 \n",
    "room_number" : "104"
},
{
    "club_name" : "Shark Tank Club\n", 
    "category" : "Competitive\n", 
    "desc" : "The shark tank club will give students various resources to prepare them for various buisness competitions and give students a chance to work with others  on their buisness ideas. The shark tank club will also allow students to work on their pitches, through our mock shark tank sessions.\n", 
    "room" : "Monday's Bi-weekly @lunch in rm 413\n",
    "room_number" : "413"
}
    ],
			mapboxes:[
{
    "x" : "13.13333333%", 
    "y" : "28.86666667%", 
    "width" : "20.06666667%", 
    "height" : "22.86666667%", 
    "name" : "Parking lot"
},{
    "x" : "34%", 
    "y" : "26.13333333%", 
    "width" : "14.06666667%", 
    "height" : "20.06666667%", 
    "name" : "Auxiliary gym"
},{
    "x" : "44.06666667%", 
    "y" : "33.6%", 
    "width" : "1.933333333%", 
    "height" : "3.666666667%", 
    "name" : "801"
},{
    "x" : "45.93333333%", 
    "y" : "33.6%", 
    "width" : "2.2%", 
    "height" : "3.666666667%", 
    "name" : "802"
},{
    "x" : "47.73333333%", 
    "y" : "33.6%", 
    "width" : "2.066666667%", 
    "height" : "3.666666667%", 
    "name" : "803"
},{
    "x" : "49.8%", 
    "y" : "33.6%", 
    "width" : "2.6%", 
    "height" : "3.666666667%", 
    "name" : "804"
},{
    "x" : "52.06666667%", 
    "y" : "33.6%", 
    "width" : "2.2%", 
    "height" : "3.666666667%", 
    "name" : "805"
},{
    "x" : "54%", 
    "y" : "33.6%", 
    "width" : "2.266666667%", 
    "height" : "3.666666667%", 
    "name" : "806"
},{
    "x" : "56%", 
    "y" : "33.6%", 
    "width" : "2.2%", 
    "height" : "3.666666667%", 
    "name" : "b"
},{
    "x" : "28.86666667%", 
    "y" : "39.93333333%", 
    "width" : "4.133333333%", 
    "height" : "3.866666667%", 
    "name" : "Weight room"
},{
    "x" : "35.86666667%", 
    "y" : "42.86666667%", 
    "width" : "5.733333333%", 
    "height" : "8.066666667%", 
    "name" : "Swimming pool"
},{
    "x" : "46.8%", 
    "y" : "39.73333333%", 
    "width" : "2.133333333%", 
    "height" : "2.866666667%", 
    "name" : "704/724"
},{
    "x" : "49.06666667%", 
    "y" : "39.73333333%", 
    "width" : "2.666666667%", 
    "height" : "2.933333333%", 
    "name" : "705/725"
},{
    "x" : "51.46666667%", 
    "y" : "39.73333333%", 
    "width" : "2.6%", 
    "height" : "2.933333333%", 
    "name" : "706/726"
},{
    "x" : "5.8%", 
    "y" : "46.66666667%", 
    "width" : "3.4%", 
    "height" : "3.866666667%", 
    "name" : "618"
},{
    "x" : "10.86666667%", 
    "y" : "46.13333333%", 
    "width" : "2.8%", 
    "height" : "2.866666667%", 
    "name" : "119"
},{
    "x" : "13.8%", 
    "y" : "46.13333333%", 
    "width" : "3.4%", 
    "height" : "2.866666667%", 
    "name" : "121"
},{
    "x" : "17.06666667%", 
    "y" : "46.13333333%", 
    "width" : "3.4%", 
    "height" : "2.8%", 
    "name" : "123"
},{
    "x" : "20.86666667%", 
    "y" : "46.13333333%", 
    "width" : "4.6%", 
    "height" : "2.8%", 
    "name" : "125"
},{
    "x" : "5.8%", 
    "y" : "50.33333333%", 
    "width" : "3.4%", 
    "height" : "3.933333333%", 
    "name" : "617"
},{
    "x" : "10.86666667%", 
    "y" : "49.2%", 
    "width" : "2.8%", 
    "height" : "3.666666667%", 
    "name" : "117"
},{
    "x" : "14.26666667%", 
    "y" : "49.2%", 
    "width" : "4.266666667%", 
    "height" : "3.6%", 
    "name" : "116"
},{
    "x" : "17.4%", 
    "y" : "48.73333333%", 
    "width" : "2.533333333%", 
    "height" : "2.866666667%", 
    "name" : "118"
},{
    "x" : "20.86666667%", 
    "y" : "48.73333333%", 
    "width" : "4.6%", 
    "height" : "2.866666667%", 
    "name" : "120"
},{
    "x" : "26.86666667%", 
    "y" : "45.6%", 
    "width" : "2.466666667%", 
    "height" : "2.6%", 
    "name" : "321"
},{
    "x" : "28%", 
    "y" : "48.86666667%", 
    "width" : "4.733333333%", 
    "height" : "9.133333333%", 
    "name" : "Girls locker"
},{
    "x" : "36.06666667%", 
    "y" : "50.4%", 
    "width" : "7.133333333%", 
    "height" : "4.8%", 
    "name" : "Small gym"
},{
    "x" : "42.73333333%", 
    "y" : "48.53333333%", 
    "width" : "1.533333333%", 
    "height" : "2.2%", 
    "name" : "AD"
},{
    "x" : "44.26666667%", 
    "y" : "48.86666667%", 
    "width" : "4.6%", 
    "height" : "9.133333333%", 
    "name" : "Boys locker"
},{
    "x" : "49.26666667%", 
    "y" : "43.46666667%", 
    "width" : "2.6%", 
    "height" : "2.933333333%", 
    "name" : "703/723"
},{
    "x" : "49.26666667%", 
    "y" : "46.2%", 
    "width" : "2.6%", 
    "height" : "2.933333333%", 
    "name" : "702/722"
},{
    "x" : "49.26666667%", 
    "y" : "48.73333333%", 
    "width" : "2.6%", 
    "height" : "2.733333333%", 
    "name" : "701/721"
},{
    "x" : "49.26666667%", 
    "y" : "51.46666667%", 
    "width" : "2.6%", 
    "height" : "3.2%", 
    "name" : "700/720"
},{
    "x" : "54.33333333%", 
    "y" : "43.46666667%", 
    "width" : "2.666666667%", 
    "height" : "2.866666667%", 
    "name" : "707/727"
},{
    "x" : "54.4%", 
    "y" : "46.06666667%", 
    "width" : "2.666666667%", 
    "height" : "2.733333333%", 
    "name" : "708/728"
},{
    "x" : "53.53333333%", 
    "y" : "48.86666667%", 
    "width" : "4.666666667%", 
    "height" : "2.866666667%", 
    "name" : "709/729"
},{
    "x" : "52.53333333%", 
    "y" : "51.53333333%", 
    "width" : "2.733333333%", 
    "height" : "2.866666667%", 
    "name" : "711/730"
},{
    "x" : "54.73333333%", 
    "y" : "51.53333333%", 
    "width" : "2.133333333%", 
    "height" : "2.866666667%", 
    "name" : "710/730"
},{
    "x" : "5.8%", 
    "y" : "54.53333333%", 
    "width" : "3.4%", 
    "height" : "4.8%", 
    "name" : "616"
},{
    "x" : "10.93333333%", 
    "y" : "52.66666667%", 
    "width" : "2.8%", 
    "height" : "3.6%", 
    "name" : "115"
},{
    "x" : "13.46666667%", 
    "y" : "52.66666667%", 
    "width" : "2.733333333%", 
    "height" : "3.6%", 
    "name" : "114"
},{
    "x" : "10.93333333%", 
    "y" : "56.2%", 
    "width" : "2.8%", 
    "height" : "3.933333333%", 
    "name" : "113"
},{
    "x" : "13.46666667%", 
    "y" : "56.2%", 
    "width" : "2.733333333%", 
    "height" : "3.933333333%", 
    "name" : "112"
},{
    "x" : "19.53333333%", 
    "y" : "54.73333333%", 
    "width" : "5.266666667%", 
    "height" : "6.4%", 
    "name" : "Sc. Quad"
},{
    "x" : "6.333333333%", 
    "y" : "61.73333333%", 
    "width" : "3.333333333%", 
    "height" : "2.6%", 
    "name" : "612"
},{
    "x" : "6.333333333%", 
    "y" : "64.2%", 
    "width" : "3.333333333%", 
    "height" : "2.666666667%", 
    "name" : "611"
},{
    "x" : "6.333333333%", 
    "y" : "66.6%", 
    "width" : "3.333333333%", 
    "height" : "2.6%", 
    "name" : "610"
},{
    "x" : "6.333333333%", 
    "y" : "69.06666667%", 
    "width" : "3.333333333%", 
    "height" : "2.666666667%", 
    "name" : "609"
},{
    "x" : "6.333333333%", 
    "y" : "71.46666667%", 
    "width" : "3.333333333%", 
    "height" : "2.6%", 
    "name" : "607"
},{
    "x" : "6.333333333%", 
    "y" : "73.93333333%", 
    "width" : "3.333333333%", 
    "height" : "2.666666667%", 
    "name" : "604"
},{
    "x" : "6.333333333%", 
    "y" : "76.33333333%", 
    "width" : "3.333333333%", 
    "height" : "2.6%", 
    "name" : "603"
},{
    "x" : "6.333333333%", 
    "y" : "78.8%", 
    "width" : "3.333333333%", 
    "height" : "2.666666667%", 
    "name" : "602"
},{
    "x" : "6.333333333%", 
    "y" : "81.2%", 
    "width" : "3.333333333%", 
    "height" : "2.666666667%", 
    "name" : "601"
},{
    "x" : "10.13333333%", 
    "y" : "60.53333333%", 
    "width" : "2.266666667%", 
    "height" : "1.533333333%", 
    "name" : "b"
},{
    "x" : "12.33333333%", 
    "y" : "60.53333333%", 
    "width" : "2.6%", 
    "height" : "1.533333333%", 
    "name" : "b"
},{
    "x" : "10.86666667%", 
    "y" : "62.53333333%", 
    "width" : "3.4%", 
    "height" : "2.933333333%", 
    "name" : "111"
},{
    "x" : "10.86666667%", 
    "y" : "65.53333333%", 
    "width" : "3.4%", 
    "height" : "3.6%", 
    "name" : "110"
},{
    "x" : "10.86666667%", 
    "y" : "69.06666667%", 
    "width" : "3.4%", 
    "height" : "3.866666667%", 
    "name" : "109"
},{
    "x" : "10.93333333%", 
    "y" : "73.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "107"
},{
    "x" : "10.93333333%", 
    "y" : "75.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.2%", 
    "name" : "105"
},{
    "x" : "10.93333333%", 
    "y" : "78.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "103"
},{
    "x" : "10.93333333%", 
    "y" : "80.4%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "101"
},{
    "x" : "13.2%", 
    "y" : "73.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "108"
},{
    "x" : "13.2%", 
    "y" : "75.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "106"
},{
    "x" : "13.2%", 
    "y" : "78.33333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "104"
},{
    "x" : "13.2%", 
    "y" : "80.4%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "102"
},{
    "x" : "18.86666667%", 
    "y" : "60.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "215"
},{
    "x" : "18.86666667%", 
    "y" : "62.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "213"
},{
    "x" : "18.86666667%", 
    "y" : "65.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "211"
},{
    "x" : "18.86666667%", 
    "y" : "67.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "209"
},{
    "x" : "18.86666667%", 
    "y" : "70.4%", 
    "width" : "2.466666667%", 
    "height" : "1.466666667%", 
    "name" : "b"
},{
    "x" : "21.06666667%", 
    "y" : "60.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "216"
},{
    "x" : "21.06666667%", 
    "y" : "62.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "214"
},{
    "x" : "21.06666667%", 
    "y" : "65.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "212"
},{
    "x" : "21.06666667%", 
    "y" : "67.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "210"
},{
    "x" : "21.06666667%", 
    "y" : "70.4%", 
    "width" : "2.466666667%", 
    "height" : "1.466666667%", 
    "name" : "b"
},{
    "x" : "26.93333333%", 
    "y" : "55.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "319"
},{
    "x" : "26.93333333%", 
    "y" : "57.6%", 
    "width" : "2.466666667%", 
    "height" : "2.2%", 
    "name" : "317"
},{
    "x" : "26.93333333%", 
    "y" : "60.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.2%", 
    "name" : "315"
},{
    "x" : "26.93333333%", 
    "y" : "62.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "313"
},{
    "x" : "26.93333333%", 
    "y" : "65.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "311"
},{
    "x" : "26.93333333%", 
    "y" : "67.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.2%", 
    "name" : "309"
},{
    "x" : "29.2%", 
    "y" : "55.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "320"
},{
    "x" : "29.2%", 
    "y" : "57.6%", 
    "width" : "2.466666667%", 
    "height" : "2.2%", 
    "name" : "318"
},{
    "x" : "29.2%", 
    "y" : "60.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "316"
},{
    "x" : "29.2%", 
    "y" : "62.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "314"
},{
    "x" : "29.2%", 
    "y" : "65.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "312"
},{
    "x" : "29.2%", 
    "y" : "67.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "TC"
},{
    "x" : "34.13333333%", 
    "y" : "53.4%", 
    "width" : "1.466666667%", 
    "height" : "1.4%", 
    "name" : "b"
},{
    "x" : "38.2%", 
    "y" : "53.4%", 
    "width" : "1.466666667%", 
    "height" : "1.4%", 
    "name" : "b"
},{
    "x" : "36.13333333%", 
    "y" : "58.4%", 
    "width" : "7.4%", 
    "height" : "10.73333333%", 
    "name" : "Large Gym"
},{
    "x" : "43.13333333%", 
    "y" : "55.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "419"
},{
    "x" : "43.13333333%", 
    "y" : "57.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "417"
},{
    "x" : "43.13333333%", 
    "y" : "60.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "415"
},{
    "x" : "43.13333333%", 
    "y" : "62.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "413"
},{
    "x" : "43.13333333%", 
    "y" : "65.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "411"
},{
    "x" : "43.13333333%", 
    "y" : "67.86666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "409"
},{
    "x" : "45.46666667%", 
    "y" : "55.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "420"
},{
    "x" : "45.46666667%", 
    "y" : "57.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "418"
},{
    "x" : "45.46666667%", 
    "y" : "60.6%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "416"
},{
    "x" : "45.46666667%", 
    "y" : "62.66666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "414"
},{
    "x" : "45.46666667%", 
    "y" : "65.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "412"
},{
    "x" : "45.46666667%", 
    "y" : "67.86666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "410"
},{
    "x" : "52.26666667%", 
    "y" : "55.6%", 
    "width" : "4.6%", 
    "height" : "2.2%", 
    "name" : "518"
},{
    "x" : "52.26666667%", 
    "y" : "57.46666667%", 
    "width" : "4.6%", 
    "height" : "2.2%", 
    "name" : "517"
},{
    "x" : "51.2%", 
    "y" : "60.73333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "515"
},{
    "x" : "51.2%", 
    "y" : "62.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "513"
},{
    "x" : "51.2%", 
    "y" : "65.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "511"
},{
    "x" : "51.2%", 
    "y" : "67.86666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "509"
},{
    "x" : "51.2%", 
    "y" : "70.46666667%", 
    "width" : "2.4%", 
    "height" : "1.4%", 
    "name" : "b"
},{
    "x" : "51.2%", 
    "y" : "73.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "507"
},{
    "x" : "51.2%", 
    "y" : "75.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "505"
},{
    "x" : "51.2%", 
    "y" : "78.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "503"
},{
    "x" : "51.2%", 
    "y" : "80.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "501"
},{
    "x" : "53.46666667%", 
    "y" : "60.73333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "516"
},{
    "x" : "53.46666667%", 
    "y" : "62.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "514"
},{
    "x" : "53.46666667%", 
    "y" : "65.8%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "512"
},{
    "x" : "53.46666667%", 
    "y" : "67.86666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "510"
},{
    "x" : "53.46666667%", 
    "y" : "70.46666667%", 
    "width" : "2.4%", 
    "height" : "1.4%", 
    "name" : "b"
},{
    "x" : "53.46666667%", 
    "y" : "73.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "508"
},{
    "x" : "53.46666667%", 
    "y" : "75.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "506"
},{
    "x" : "53.46666667%", 
    "y" : "78.46666667%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "504"
},{
    "x" : "53.46666667%", 
    "y" : "80.53333333%", 
    "width" : "2.466666667%", 
    "height" : "2.266666667%", 
    "name" : "502"
},{
    "x" : "34%", 
    "y" : "75.6%", 
    "width" : "7.4%", 
    "height" : "11.73333333%", 
    "name" : "Main Quad"
},{
    "x" : "45.06666667%", 
    "y" : "71.73333333%", 
    "width" : "6.266666667%", 
    "height" : "2.733333333%", 
    "name" : "Admin"
},{
    "x" : "42.93333333%", 
    "y" : "75.93333333%", 
    "width" : "6.533333333%", 
    "height" : "6.066666667%", 
    "name" : "Library"
},{
    "x" : "47.06666667%", 
    "y" : "75.93333333%", 
    "width" : "2.2%", 
    "height" : "6.066666667%", 
    "name" : "TBC"
},{
    "x" : "43.66666667%", 
    "y" : "80.2%", 
    "width" : "3.333333333%", 
    "height" : "2.933333333%", 
    "name" : "Kip office"
},{
    "x" : "46.66666667%", 
    "y" : "80.2%", 
    "width" : "3.066666667%", 
    "height" : "2.933333333%", 
    "name" : "Admin"
},{
    "x" : "33.8%", 
    "y" : "90.4%", 
    "width" : "7.733333333%", 
    "height" : "8.933333333%", 
    "name" : "Theater"
},{
    "x" : "41.26666667%", 
    "y" : "90.33333333%", 
    "width" : "7.6%", 
    "height" : "8.933333333%", 
    "name" : "Cafeteria"
},{
    "x" : "49.4%", 
    "y" : "88.73333333%", 
    "width" : "5.933333333%", 
    "height" : "5.4%", 
    "name" : "Packard Hall"
},{
    "x" : "61.73333333%", 
    "y" : "89.26666667%", 
    "width" : "2.4%", 
    "height" : "4.533333333%", 
    "name" : "P1"
},{
    "x" : "64%", 
    "y" : "89.26666667%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P2"
},{
    "x" : "66.26666667%", 
    "y" : "89.26666667%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P3"
},{
    "x" : "68.53333333%", 
    "y" : "89.26666667%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P4"
},{
    "x" : "70.8%", 
    "y" : "89.26666667%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P5"
},{
    "x" : "73.06666667%", 
    "y" : "89.26666667%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P6"
},{
    "x" : "62.46666667%", 
    "y" : "94.2%", 
    "width" : "4.266666667%", 
    "height" : "4.533333333%", 
    "name" : "P7"
},{
    "x" : "65.6%", 
    "y" : "94.2%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P8"
},{
    "x" : "67.86666667%", 
    "y" : "94.2%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P9"
},{
    "x" : "70.13333333%", 
    "y" : "94.2%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P10"
},{
    "x" : "72.4%", 
    "y" : "94.2%", 
    "width" : "2.466666667%", 
    "height" : "4.533333333%", 
    "name" : "P11"
},{
    "x" : "16.66666667%", 
    "y" : "90.4%", 
    "width" : "22.93333333%", 
    "height" : "14.73333333%", 
    "name" : "Parking lot"
}
    ],

		}
	  },
	  components:{
          VButton,
		  MapBox,
		  VInput,
      },
      methods:{
          goToAbout(){
              window.location.href = "/about";
          },
		  goToMap(){
            window.location.href = "/map";
			},
		selectClubs(){
			document.getElementById("ClubsView").style.backgroundColor="#c2ffd3";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.remove("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="clubs";
			
		},
		selectLunch(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="#c2ffd3";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.remove("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="lunch";
		},
		selectTeachers(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="#c2ffd3";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.remove("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="teachers";
		},
		selectEvents(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="#c2ffd3";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.remove("notSelected");
			this.view="events";
		},
		displayInfo(room_name){
            document.getElementById("info").innerHTML = "Clubs:<br>";
            //clubs
			for (var i=0; i<this.clubs.length; i++) {
                if (this.clubs[i]["room_number"] == room_name)
                document.getElementById("info").innerHTML += this.clubs[i]["club_name"] + ": " +this.clubs[i]["room"]  + "<br><br>";
            }
            //teachers
            for (var i=0; i<this.clubs.length; i++) {
                if (this.clubs[i]["room_number"] == room_name)
                document.getElementById("info").innerHTML += this.clubs[i]["club_name"] + ": " +this.clubs[i]["room"]  + "<br><br>";
            }
		}
		
      },
      created(){
		var rooms=[];
		for(var i=0;i<this.clubs.length;i++){
			rooms.push(this.clubs[i].room_number);
		}
		
		for(var i=0;i<this.mapboxes.length;i++){
			if(rooms.includes(this.mapboxes[i].name)){
				this.mapboxes[i].on="true";
			}
		}
		
      },
  }
</script>
  
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600&display=swap');
  #Pitch{
      font-family: 'Open Sans', sans-serif;
      font-size:80px;
      font-weight:600;
      position:absolute;
      width:50%;
      height:10%;
      left:0%;
      top:25%;
      text-align:center;
  }
  #Pitch2{
      font-family: 'Open Sans', sans-serif;
      font-size:100px;
      font-weight:600;
      position:absolute;
      width:50%;
      height:15%;
      left:0%;
      top:35%;
      text-align:center;
  }
  #SubPitch{
      font-family: 'Open Sans', sans-serif;
      font-size:30px;
      font-weight:500;
      position:absolute;
      width:50%;
      height:10%;
      left:0%;
      top:55%;
      text-align:center;
  }
  .linear-wipe {
    background: linear-gradient(
          to right,
          #00db96 20%,
          #00affa 30%,
          #0190cd 70%,
          #00db66 80%
      );
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      text-fill-color: transparent;
      background-size: 500% auto;
      animation: textShine 3s ease-in-out infinite alternate;
  }
  @keyframes textShine {
      0% {
          background-position: 0% 50%;
      }
      100% {
          background-position: 100% 50%;
      }
  }
  #MapArt{
      width:40%;
      position:absolute;
      left:50%;
      top:20%;
      animation-name:float;
      animation-duration:3s;
      animation-iteration-count:infinite;
      animation-timing-function:ease;
  }
  @keyframes float{
      0% { transform: translate(0,  0px); }
      50%  { transform: translate(0px, 25px); }
      100%   { transform: translate(-0, -0px); }   
  }
  #Home{
      width:20%;
      position:absolute;
      left:0%;
      height:10%;
      top:0%;
      display:flex;
      align-items:center;
      text-align:left;
      text-decoration:none;
      padding-left:40px;
      padding-top:10px;
      font-family: 'Open Sans', sans-serif;
      font-size:40px;
      font-weight:600;
      color:black;
  }
  #HeaderSeparator{
      background-color:rgba(0,0,0,0.1);
      width:100%;
      position:absolute;
      left:0%;
      top:12%;
      height:2px;
  }
  #RightSeparator{
      background-color:rgba(0,0,0,0.1);
      height:88%;
      position:absolute;
      left:75%;
      top:12%;
		width:2px;
  }
  #Map{
	height:100%;
	position:absolute;
	top:0%;
	left:30%;
	
  }
  #BoxContainer{
	height:100%;
	position:absolute;
	top:0%;
	left:30%;
	width:952px;
  }
  #ViewSelector{
	border:2px solid rgba(0,0,0,0.1);
	position:absolute;
	left:2%;
	top:65%;
	width:10%;
	height:30%;
	border-radius:5px;
  }
  #ClubsView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:0%;
	background-color:#c2ffd3;
	color:black;
	
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
  
  #LunchView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:25%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
  
  #TeachersView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:50%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
   
  .notSelected:hover{
	filter:brightness(70%);
  }
  #EventsView{
	width:100%;
	border-bottom:none;
	height:25%;
	position:absolute;
	left:0%;
	top:75%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
   
  #ViewLabel{
	position:absolute;
	width:100%;
	text-align:center;
	top:-15%;
	font-family: 'Open Sans', sans-serif;
	font-size:20px;
	font-weight:500;
	opacity:0;
  }
  #info{
    position:absolute;
    left:77%;
    top:15%;
    font-family: 'Open Sans', sans-serif;

  }


</style>
  
  