From the `mystery` directory:

# 1) Get all real clues from the crimescene file:
`grep "^CLUE:" crimescene`

    CLUE: Footage from an ATM security camera is blurry but shows that the perpetrator is a tall male, at least 6'.

    CLUE: Found a wallet believed to belong to the killer: no ID, just loose change, and membership cards for AAA, Delta SkyMiles, the local library, and the Museum of Bash History. The cards are totally untraceable and have no name, for some reason.

    CLUE: Questioned the barista at the local coffee shop. He said a woman left right before they heard the shots. The name on her latte was Annabel, she had blond spiky hair and a New Zealand accent.

-----
# 2) Find all Annabels:
`grep "Annabel" people`

    Annabel Sun	        F	26	Hart Place, line 40
    Oluwasegun Annabel	M	37	Mattapan Street, line 173
    Annabel Church	        F	38	Buckingham Place, line 179
    Annabel Fuglsang	M	40	Haley Street, line 176

-----
# 3) Get addresses of the females named Annabel: 
`head -n 40 "streets/Hart_Place" | tail -n 1`

    SEE INTERVIEW #47246024
`head -n 179 "streets/Buckingham_Place" | tail -n 1`
    
    SEE INTERVIEW #699607

-----
# 4) Get contents of interview whose file name ends with 47246024 and 699607:
`cat  ./interviews/*47246024*`

    Ms. Sun has brown hair and is not from New Zealand.  Not the witness from the cafe.

`cat  ./interviews/*699607*`

    Interviewed Ms. Church at 2:04 pm.  Witness stated that she did not see anyone she could identify as the shooter, that she ran away as soon as the shots were fired.
    However, she reports seeing the car that fled the scene.  Describes it as a blue Honda, with a license plate that starts with "L337" and ends with "9"

# 5) Find Vehicle with licence plate that begins with L337 and ends with 9:
`grep -A5 "License Plate L337" vehicles`

(Manually delete all females, people less than 6' and cars that aren't blue hondas ...)

    License Plate L337DV9
    Make: Honda
    Color: Blue
    Owner: Joe Germuska
    Height: 6'2"
    Weight: 164 lbs
    --
    License Plate L3375A9
    Make: Honda
    Color: Blue
    Owner: Jeremy Bowers
    Height: 6'1"
    Weight: 204 lbs

# 6) Get more info about Joe Germuska and Jeremy Bowers:
`grep "Joe Germuska" people`

    Joe Germuska       M       65      Plainfield Street, line 275

`grep "Jeremy Bowers" people`

    Jeremy Bowers      M       34      Dunstable Road, line 284

# 7) Get their addresses:
`head -n 275 "streets/Plainfield_Street" | tail -n 1`

    SEE INTERVIEW #29741223

`head -n 284 "streets/Dunstable_Road" | tail -n 1`

    SEE INTERVIEW #9620713

# 8) Read Interviews #9620713 and #29741223:  
`cat ./interviews/*29741223*`      

    (Joe Germuska)
    Should not be considered a suspect, has no SkyMiles membership and has never been a member of the Museum of Bash History.

`cat ./interviews/*9620713*`

    (Jeremy Bowers)
    Home appears to be empty, no answer at the door.
    After questioning neighbors, appears that the occupant may have left for a trip recently.
    Considered a suspect until proven otherwise, but would have to eliminate other suspects to confirm.

# 9) The suspect is Jeremy Bowers
`echo "Jeremy Bowers" | $(command -v md5 || command -v md5sum) | grep -qif /dev/stdin ../encoded && echo CORRECT\! GREAT WORK, GUMSHOE. || echo SORRY, TRY AGAIN.`

    CORRECT! GREAT WORK, GUMSHOE.


**- Ikey Benz**