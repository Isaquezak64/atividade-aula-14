//# atividade-aula-14
//Aula 14 de abril de 2025 - Tutorial back-end


const imoveis = [
    {
        id: 1,
        endereco: "rua da abobora 234",
        tipo: "casa",
        valor: "200.000"
    },
    {
        id: 2,
        endereco: "rua do pneu queimado 231",
        tipo: "apto",
        valor: "100.000"
    },
    {
        id: 3,
        endereco: "",
        tipo: "",
        valor: ""
    },
];
 
 
app.get("/imoveis", (req, res) => {
 
    res.json(imoveis);
});
 
app.get("/imoveis/:id", (req, res) => {
    const id = parseInt(req.params.id);
    const imovel = imoveis.find(imovel => imovel.id === id);
    if (imovel) {
      res.json(imovel);
    } else {
      res.status(404).json({ mensagem: 'Imóvel não encontrado' });
    }
  });
  
app.post("/imoveis", (req, res) => {
    const {endereco, tipo, valor} = req.body;
    const id = imoveis.length + 1;
   imoveis.push({id, endereco, tipo, valor});
    res.status(201).location(`/imoveis/${id}`).send();
});
 
app.put("/imoveis/:id", (req, res)=> {
    const id = parseInt(req.params.id);
    const imovel = imoveis.find(imovel => imovel.id === id);
    if (imovel) {
        const {endereco , tipo, valor} = req.body;
        imovel.endereco = endereco;
        imovel.tipo = tipo;
        imovel.valor = valor;
        res.status(200).send();
    }else {
        res.status(404).send();
    }
});
 
app.delete("/imoveis/:id", (req, res)=> {
    const id = parseInt(req.params.id);
    const index = imoveis.dinfIndex(imovel => imovel.id == id);
    if (index !== -1) {
        imoveis.splice(index, 1);
        res.status(200).json({ mensagem: 'imovel removido com sucesso' });
    } else {
        res.status(404).json({ mensagem: 'imovel não encontrado' });
    }
});
 
app.patch("/imoveis/:id", (req, res) =>{
    const id = parseInt(req.params.id);
    const imovel = imoveis.find(imovel =>imovel.id === id);
    if(imovel){
        const {endereco, tipo, valor} = req.body;
        if(endereco !== undefined){
            imovel.endereco = endereco;
        }
        if(tipo !== undefined){
            imovel.preco = preco;
        }
        if(valor !== undefined){
            imovel.preco = preco;
        }
        res.status(200).json({ mensagem: 'sucesso' });
    }else{
        res.status(404).json({ mensagem: 'não foi' });
    }
})
