# MARKDOWN REACT PROJECT

## HOW TO START A REACT PROJECT
1. Open your terminal
2. Instal NPM if you don't have it install -g npm-and after create a react app with create-react-app <name>.Also there is another way only with create app adding npx create-react-app <name>
3. cd in your project
4. npm start:  to run the browser 
5. Start creating components

## PROPS
We use props to transmit information from parent (ex:<App/>) to child (ex:<Contact/>) components.
2 ways of using props:

1.First version: 
```javascript
//WITHOUT MAP:
function Contact (props){
    return (
        <figure className="Contact">
            <img className="avatar"
                src={props.avatar}
                alt={props.name} />
            <div>
                <p className="name">{props.name}</p>
                <p className="status"> 
                    {
                        props.status === "online"
                            ? <div className="status-online"></div>
                            : <div className="status-offline"></div>
                    } 
                    {props.status}
                    
                </p>
            </div>
        </figure>
    )
}
//WITH MAP:
const Contact =(props) => (
        <div>
            {props.user.map((person, index) => (
             <figure className='Contact' key={index}>
                        <img className='avatar' src={person.avatar} alt=""></img>
                        <div className='status'  >
                            <h4 className='name' >{person.name}</h4>
                            <h4 id={index} className='status-text' onClick={props.change}><span className={person.status?"status-online": "status-offline"}></span>{person.status?"online": 'ofline'}</h4> 
                        </div>
                    </figure>
            ))}
        </div>
)
```

2.Shorted and cleares way:
/*We pick up the user object using arrow function for props so we can display the user info in a JSX using a loop named MAP, so the next code we displayed x number of times dipending of the number od users are un the prop thai is saved in App.js.*/
 ```javascript
 const Contact =({user, change}) => (
        <div>
            {user.map((i, x) => (
             <figure className='Contact' key={x}>
                        <img className='avatar' src={i.avatar}alt=""></img>
                        <div className='status'  >
                            <h4 className='name' >{i.name}</h4>
                            <h4 id={x} className='status-text' onClick={change}><span className={i.status?"status-online": "status-offline"}></span>{i.status?"online": 'ofline'}</h4> 
                        </div>
                    </figure>
            ))}
        </div>
)
```

*=> Both methods receive the props from App render where we insert <Contact> with the props names
```javascript
render() {
  return (
    <div>
      <Contact user={this.state.users} change={this.changeStatus}/>
    </div>
  );
}
}
```
 ## STATE 
 The main diference with props is that we use state for updating props info with diferent methods that we use for example by using events such as onClick or onMouseOver.

 ```javascript
 state=
  {name:'Ana',
   status:false,
   avatar:'https://avatars0.githubusercontent.com/u/9919?s=280&v=4'
   }
   ```
 So the state is an object with information that can be changed by calling the state (using setState() because directly using this.state it's imposible)
 For example:
 ```javascript
doSomthing = () => {
  this.setState({
      [this.state.users]: 'something new'
    }) 
 }
 ```
 It's not necesary to write constructor for declaring the state, unless you use the functions without arrow function. Then you have to put 
 
 ```javascript
 constuctor(){
     super(props)
     this.state =  {name:'Ana',
   status:false,
   avatar:'https://avatars0.githubusercontent.com/u/9919?s=280&v=4'
   }
   //and put this for the function, because if not it doesn't work
   this.doSomthing=this.doSomthing.bind()
 }
 ```
 ## API 
TO BE CONTINUED....
    

