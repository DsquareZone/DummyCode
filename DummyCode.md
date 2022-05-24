````
import React, {useState} from 'react';
import {AgGridColumn, AgGridReact} from 'ag-grid-react';
import 'ag-grid-community/dist/styles/ag-grid.css';
import 'ag-grid-community/dist/styles/ag-theme-alpine.css';
import './Moviegrid.css'

const InitialRowData = [
    {movie: "The Shawshunk Redemption", year: 1994, rating: 9.2},
    {movie: "The Godfather 1", year: 1972, rating: 9.2},
    {movie: "The Dark Knight", year: 2008, rating: 9.0},
    {movie: "The Godfather 2", year: 1974, rating: 9.0},
    {movie: "12 Angry Men", year: 1972, rating: 9.2},
    {movie: "Lord of ring", year: 2003, rating: 9.0},
    {movie: "Schlinder's List", year: 1994, rating: 8.9},
    {movie: "The Pulp fiction", year: 1994, rating: 8.9},
    {movie: "Forest Gump", year: 1984, rating: 8.8},
    {movie: "Flight Club", year: 1999, rating: 8.8},
    {movie: "Inception", year: 2010, rating: 8.7},
    {movie: "The Matrix", year: 2008, rating: 8.7} 
];

export function Moviegrid() {

    const [rowData, setRowData] = useState(InitialRowData);
    React.useEffect(() => {
        fetch('')
            .then(result => result.json())
            .then(rowData => setRowData(rowData))
    }, []);
    
    
    const [colDefs, setColDefs] = useState([
        {field: 'movie'},
        {field: 'year'},
        {field: 'rating', editable: 'true'},
        fetch('http://localhost:3000/')
            .then(result => result.json())
            .then(colDefs => setColDefs(colDefs))
    ]);
    
    
    

   return (
       <center>

           <h1>Movies Ratings 2022</h1>

       <div className="ag-theme-alpine" style={{height: 500, width: 800,}}>   
           <AgGridReact defaultColDef={{sortable: true, filter: true,floatingFilter:true }}pagination={true}
                rowData={rowData} columnDefs={colDefs} checkboxSelection={true}>
                 </AgGridReact>

                <AgGridColumn field="movie" defaultColDef={{sortable: true, filter: true}}
                pagination={true}
                rowData={rowData}
                columnDefs={colDefs}>   
                </AgGridColumn>
                
                <AgGridColumn field="year" 
                defaultColDef={{sortable: true, filter: true}}
                pagination={true}
                rowData={rowData}
                columnDefs={colDefs}
                checkboxSelection={true}
                >
                </AgGridColumn>
                
                <AgGridColumn field="rating"  Sortablesortable={true} checkboxSelection={true} ></AgGridColumn>
           </div>
       </center>
   )
};
````
