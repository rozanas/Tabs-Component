# Tabs-Component
import App from './App';

ReactDOM.render(<App />, document.getElementById('react-root') );
import Xtab from './components/xtabs';

function App() {
    const items = [
    {
        name: "Tab 1",
        content: (
        <>
            <h4>This is tab one</h4>
            <p>Lorem </p>
        </>
        ),
        is_active: true,
    },
    {
        name: "Tab 2",
        content: ( <p>This is tab 2</p> ),
        is_active: false,
    },
    ];

    return (
        <Xtab items={items} />
    );
}

export default App;
const [items, setItems] = useState( props.items )
function show(event, index){
    let tabs = items;

    tabs.map( ( item, item_index ) => {

        item.is_active=false
        if( item_index == index ){
            item.is_active=true
        }

        return tabs
    } )

    setItems( [ ...tabs ] )
}
import React, { useState } from 'react'
import  styles from './xtabs.module.css'

export default function Xtab( props ) {

    const [items, setItems] = useState( props.items )

    function show(event, index){
        let tabs = items;

        tabs.map( ( item, item_index ) => {

            item.is_active=false
            if( item_index == index ){
                item.is_active=true
            }

            return tabs
        } )

        setItems( [ ...tabs ] )
    }


    return (
        <React.Fragment>
            <div className={ styles['x-tab'] } >
                <ul className={ styles['x-tab-list'] }>
                    {
                        items.map( ( item, index ) => {
                            return  (
                                <li key={index} onClick={ ( event ) => show( event, index ) }
                                    className={ ` ${ styles['x-tab-item'] } ${ ( item['is_active'] )? styles['active'] : '' } ` } >
                                    <span>{ item['name'] }</span>
                                </li>
                            )
                        } )
                    }

                </ul>

                <div className={ styles['x-tab-container'] } >

                    {
                        items.map( ( item, index ) => {
                            return  (
                                <div key={index} className={ ` ${ styles['x-tab-content'] }  ${ ( item['is_active'] )? styles['active'] : '' } ` }>
                                    { item['content'] }
                                </div>
                            )
                        } )
                    }
                </div>
            </div>
        </React.Fragment>
    )
}
.x-tab{
    background-color: #fcfcfc;
}

.x-tab .x-tab-list{
    margin: 0;
    padding: 0;
    display: flex;
}

.x-tab .x-tab-item{
    display: inline-block;
    padding: 10px 15px;
    cursor: pointer;
}

.x-tab .x-tab-item.active{
    background-color: #ebebeb;
}

.x-tab .x-tab-container{
    display:block;
}

.x-tab .x-tab-content{
    display: none;
}

.x-tab .x-tab-content.active{
    display: block;
    padding: 10px 15px;
}
