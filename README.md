**  Milestone 2 TO DO:**

Eliminated Person and RPC-Guess Name have been implemented. After user makes a guess, 
server will simply tell client if the guess is correct or not. The GAME STATE
logic has NOT yet been implemented on either side. 

- Update Game state on Server side
  - After server processes the Guess-Name-RPC, server needs to update game state.

- Update Game State on Client side 
  - Menu logic needs to be reviewed. 
    - Eg. what should happen if user wants to start another game (under the same login)
    - Eg. what should happen if user wins or loses?
  - Does Client need to know Game ID?
  
- Mutex application 
  - Server >> Create a map of <GameID, Game>, possibly in the Global context class 
  - Server >> Create two "GAME STATE": "IN-PROGRESS", "ENDED" (?)
    - Possibly add a boolean "Game state" field to Game class 
  - Server >> After a Game is created, set game state to "IN-PROGRESS"
  - Server >> After a player has won, set game state to "ENDED"
  - Use mutex locker to ensure only one "GAME STATE" is updated at once
  
**- Powerpoint presentation can be started!
**
- CMakeFile

- Troubleshooting (as time allows)
  - clarify Client number discrepency between server and client (I suspect the socketID generated by the client and server is not identical)



**Milestone 2 already done:**
- Server >> Game class created on Server side 
- Server >> Character class created on Server side 
- added new RPC called ```getCharacterList```
- renamed getCharacterList function
- added RPCImpl::rpcGetTraitList()
- added RPCImpl::getTraitNames()
- added Character::getTraitNames() to support RPCImpl::getTraitNames()
- updated Game::setSourceList() to call Game::addCharacter()
- added RPCImpl::rpcQueryTrait()
- added new RPC called ```getTraitList```


- Finished implementing RPC QueryTrait
  - Implemented Client::queryTrait() function
  - Added Client::getQueryTraitName() function
  - Added Client::getQueryTraitValue() function (Customized user questions based on traitName selected)
  - Added Client::validateUserInput() function
  - Added Client::formatAnswer() function to standardize "queryTrait message" to make this RPC easier to process
  - Added Client::trim() function to trim leading and trailing zeros
  - Edited RPCImpl::rpcQueryTrait() function to be responsible for parsing "queryTrait" message
  - Moved query checking to new function RPCImpl::queryTraitResponse()
  - Added customized server response in RPCImpl::customizedReply() function
  

- Server: Cleanup up console output for server to group RPCs into logical text blocks in display window
- Client: Modified displayCharacterList() in ClientMain to display characters and traits as a table
- Client: Created a 2D vector to hold the trait values for each character.


- Populated active list table on Client side
  - Added Client::getTraitValuesFromServer() function
  - Added RPCImpl::rpcGetTraitValues() function
  - Adjusted data types of a couple of fields in Game class, Character class, and Client.h to facilitate RPC process, key value retrieval, and printing.
- Implemented Eliminate Person 
  - Added Client::eliminatePerson() function to eliminate character rows locally
  - Added Client::getEliminateChoice() function to get user choice, user input validation included
- Implemented RPC-Guess Name 
  - Added Client::guessName() function to send final guess to server and get response
  - Added Client::getUserGuess() function to get user guess
  - Added RPCImpl::rpcFinalGuess() function to process user guess
  
