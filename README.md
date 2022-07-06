# BBIT

%%writefile ../implementations/accountSolution.py 
#Uncomment line above & run cell to save solution
#TODO Define class that implements accountInterface & allows for the management of an account

def account:
    def __init__(self, positions, accountName):
        self.accountName = accountName
        self._set = set(positions)
        
    def getName(self):
        return self.accountName
    
    def getAllPositions(self):
        return self._set
    
    def getPositions(self, securities):
        for i in securities:
            if isinstance(i, (str)):
                if i.getPosition() in self._set:
                    
  
  %%writefile ../implementations/positionSolution.py 
#Uncomment line above & run cell to save solution
#TODO Define class that implements positionInterface & allows for the management of a position
from implementations.securitySolution import security
class position:
    def __init__(self, secure, initialPosition):
        if isinstance(secure, security):
            self.sec = secure
        
        if isinstance(secure, (str)):
            self.sec = security(secure)
        
        self.initialPosition = initialPosition
    
    def getSecurity(self):
        return self.sec
    
    def getPosition(self):
        return self.initialPosition
    
    def setPosition(self, newPosition):
        self.initialPosition = newPosition
        
    def addPosition(self, newPosition):
        self.initialPosition = newPosition + self.initialPosition
        if self.initialPosition < 0:
            raise ValueError("Expect positive position")
        
    
    
  %%writefile ../implementations/securitySolution.py 
#Uncomment line above & run cell to save solution
#TODO Define class that implements securityInterface & allows for the management of a security
class security:
    def __init__(self, name):
        self.name = name
        
    def setName(self, a):
        print("set name method called")
        self.name = a
    
    def getName(self):
        print("get name method called")
        return self.name
