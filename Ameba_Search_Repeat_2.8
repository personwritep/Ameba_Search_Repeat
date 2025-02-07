// ==UserScript==
// @name        Ameba Search Repeat
// @namespace        http://tampermonkey.net/
// @version        2.8
// @description        ブログ内検索の再検索を実行可能にする
// @author        Ameba Blog User
// @match        https://search.ameba.jp/search/entry/*.html?aid=*
// @run-at        document-start
// @grant        none
// @updateURL        https://github.com/personwritep/Ameba_Search_Repeat/raw/main/Ameba_Search_Repeat.user.js
// @downloadURL        https://github.com/personwritep/Ameba_Search_Repeat/raw/main/Ameba_Search_Repeat.user.js
// ==/UserScript==


let edit_mode=0; // リストを常に再編集で開くモード

in_view(); // ページにCSSを適用


window.addEventListener('load', function(){

    let target=document.body; // 監視 target
    let monitor=new MutationObserver(check_page);
    monitor.observe(target, {childList: true}); // 検索待受け開始

    check_page();

    function check_page(){
        if(location.search.startsWith('?aid=')){
            search_next(); }
        else{
            if(document.head.querySelector('.sih')){
                document.head.querySelector('.sih').remove(); }}}});



function search_next(){ // 検索結果ページごとにURLは更新される
    let blogDB={}; // 閲覧記事のID/チェックフラグの記録配列
    let entry_id_DB; // ID検索用の配列

    let read_json=localStorage.getItem('ASR_DB_back'); // ローカルストレージ 保存名
    blogDB=JSON.parse(read_json);
    if(blogDB==null){
        blogDB=[['ASR00000000', '0']]; }

    if(blogDB[0][0]=='ASR00000001'){ // ストレージのフラグで edit_mode が「1」
        edit_mode=1; }

    if(get_userid(0) !=null){
        blogDB[0][1]=get_userid(0); } // スクリプト起動時に開いたユーザーIDを記録
    let write_json=JSON.stringify(blogDB);
    localStorage.setItem('ASR_DB_back', write_json); // ローカルストレージ 保存



    reg_set();

    function reg_set(){
        let k;
        entry_id_DB=[]; // リセット
        for(k=0; k<blogDB.length; k++){
            entry_id_DB[k]=blogDB[k][0]; }} // ID検索用の配列を作成



    focus_in(); // 検索直後は検索枠にキャレットを入れる

    function focus_in(){
        let this_url=location.href;
        let index_page=this_url.indexOf('&p=');
        if(index_page==-1){ // 検索直後の先頭ページ
            let inp=document.querySelector('.PcSuggestForm_Input');
            if(inp){
                let len=inp.value.length;
                inp.focus();
                inp.setSelectionRange(len, len); }}}



    list_set();

    function list_set(){
        let entrylist=[];
        let entrylink=[];
        let entryhref=[];
        let history=[];

        entrylist=document.querySelectorAll('.PcEntryListItem');
        for(let k=0; k<entrylist.length; k++){
            entrylink[k]=entrylist[k].querySelector('.PcEntryListItem >a');
            entryhref[k]=entrylink[k].getAttribute('href').slice(-16, -5);
            mark(k);
            list_listen(k);
            hmark_listen(k); }


        function mark(k){
            let history_='<p class="history">\u00A0</p>';
            if(entrylink[k].querySelector('.history')){
                entrylink[k].querySelector('.history').remove(); }
            entrylink[k].insertAdjacentHTML('beforeend', history_);

            history[k]=entrylink[k].querySelector('.history');
            let list_size=entrylink[k].getBoundingClientRect().height;
            let img_size=entrylist[k].querySelector('.UserThumbnail').getBoundingClientRect().height;
            let top=(list_size + img_size)/2 - 6;
            history[k].style.top=top + 'px'; // サムネイルとリストの上下間にマークを配置

            let index=entry_id_DB.indexOf(entryhref[k]);
            if(index !=-1){
                if(blogDB[index][1]==1){
                    history[k].style.background='#009688'; } // フラグ1ならグリーン
                else if(blogDB[index][1]==2){
                    history[k].style.background='#ff8800'; } // フラグ2ならオレンジ
                else if(blogDB[index][1]==0){
                    history[k].style.background='#fff'; }}} // フラグ0なら白


        function list_listen(k){
            entrylink[k].addEventListener('click', function(event){
                event.preventDefault();
                event.stopImmediatePropagation();
                all_click();
                if(edit_mode==0){ // 別タブに記事画面を開く
                    let pass=entrylink[k].getAttribute('href');
                    window.open(pass, "_blank"); }
                if(edit_mode==1){ // 別タブに再編集画面を開く
                    let pass=
                        'https://blog.ameba.jp/ucs/entry/srventryupdateinput.do?id='+entryhref[k];
                    window.open(pass, "_blank"); }}, false);

            entrylink[k].addEventListener('contextmenu', function(){
                all_click(); }, false);

            function all_click(){
                let index=entry_id_DB.indexOf(entryhref[k]);
                if(index==-1){
                    blogDB.push([entryhref[k], 1]); } // 閲覧履歴に記事ID/フラグ1を追加
                else{
                    blogDB[index]=[entryhref[k], 1]; } // この記事IDの履歴をフラグ1に更新
                let histo=document.querySelectorAll('.history');
                histo[k].style.background='#009688';
                let write_json=JSON.stringify(blogDB);
                localStorage.setItem('ASR_DB_back', write_json); // ストレージ保存
                reg_set(); }}


        function hmark_listen(k){
            history[k].addEventListener('click', function(event){
                event.preventDefault();
                event.stopImmediatePropagation();
                let index=entry_id_DB.indexOf(entryhref[k]);
                if(index==-1){
                    blogDB.push([entryhref[k], 1]); // 閲覧履歴に記事ID/フラグ1を追加
                    history[k].style.background='#009688'; } // グリーン
                else{
                    if(blogDB[index][1]==1){
                        blogDB[index]=[entryhref[k], 2]; // この記事IDの履歴をフラグ2に更新
                        history[k].style.background='#ff8800'; } // オレンジ（Noteフラグ）
                    else if(blogDB[index][1]==2){
                        blogDB[index]=[entryhref[k], 0]; // この記事IDの履歴をフラグ0に更新
                        history[k].style.background='#fff'; } // 白（履歴のフラグをリセット）
                    else if(blogDB[index][1]==0){
                        blogDB[index]=[entryhref[k], 1]; // この記事IDの履歴をフラグ1に更新
                        history[k].style.background='#009688'; }} // グリーン
                let write_json=JSON.stringify(blogDB);
                localStorage.setItem('ASR_DB_back', write_json); // ストレージ保存
                reg_set(); }, false); }

    } //  list_set()



    reset_sw();

    function reset_sw(){
        let box=document.querySelector('.PcResultPagination');
        if(box){
            let sw_=
                '<p id="history_reset">Reset</p>'+
                '<p id="sw_tooltip2">全記事の履歴マークをリセットします</p>';
            if(!box.querySelector('#history_reset')){
                box.insertAdjacentHTML('beforeend', sw_); }

            let history_reset=box.querySelector('#history_reset');
            if(history_reset){
                history_reset.onclick=function(){
                    let conf_str='🟩　リストの履歴マーク（閲覧/編集）をリセットします';
                    let ok=confirm(conf_str);
                    if(ok){
                        if(edit_mode==0){
                            blogDB=[['ASR00000000', blogDB[0][1]]]; }
                        if(edit_mode==1){
                            blogDB=[['ASR00000001', blogDB[0][1]]]; }
                        let write_json=JSON.stringify(blogDB);
                        localStorage.setItem('ASR_DB_back', write_json); // ストレージ保存
                        reg_set();
                        list_set(); }}}}}



    edit_sw();

    function edit_sw(){
        let box=document.querySelector('.PcResultPagination');
        if(box){
            let sw_=
                '<p id="edit"></p>'+
                '<p id="sw_tooltip3">記事のクリックで開く画面　Read: ブログ画面　Edit: 編集画面</p>';
            if(!box.querySelector('#edit')){
                box.insertAdjacentHTML('beforeend', sw_); }

            let edit=box.querySelector('#edit')
            if(edit){
                if(edit_mode==0){
                    edit.textContent='Read';
                    edit.style.background='#72adc8'; }
                else if(edit_mode==1){
                    edit.textContent='Edit';
                    edit.style.background='red'; }

                edit.onclick=function(){
                    let read_json=localStorage.getItem('ASR_DB_back'); // ローカルストレージ 保存名
                    blogDB=JSON.parse(read_json);

                    if(edit_mode==0){
                        edit.textContent='Edit';
                        edit.style.background='red';
                        edit_mode=1;
                        blogDB[0][0]='ASR00000001'; } // edit_mode 「1」のフラグ
                    else if(edit_mode==1){
                        edit.textContent='Read';
                        edit.style.background='#72adc8';
                        edit_mode=0;
                        blogDB[0][0]='ASR00000000'; }
                    let write_json=JSON.stringify(blogDB);
                    localStorage.setItem('ASR_DB_back', write_json); // ストレージ保存
                    reg_set();
                    list_set(); }}}}



    jump_sw();

    function jump_sw(){
        let more_l;
        let more_r;

        let more_link=document.querySelectorAll('.PcResultPagination_MoreLink');
        if(more_link.length!=0){
            if(more_link[0].querySelector('.s-triangle-left')){
                more_l=more_link[0]; }
            if(more_link[0].querySelector('.s-triangle-right')){
                more_r=more_link[0]; }
            if(more_link[1]){
                if(more_link[1].querySelector('.s-triangle-right')){
                    more_l=more_link[0];
                    more_r=more_link[1]; }}}

        let hit_str=document.querySelector('.PcEntryList .PcHitCountRange');
        if(hit_str){
            let q_str=window.location.search.split('&')[0];
            if(more_l){
                let more_lavel=more_l.querySelector('.PcResultPagination_MoveLabel');
                more_lavel.textContent='TOP';
                more_l.style.display='block';
                let jump_url=window.location.href.split('?')[0] + q_str + '&p=1';
                more_l.onclick=function(e){
                    event.preventDefault();
                    location.href=jump_url; }}
            if(more_r){
                let more_lavel=more_r.querySelector('.PcResultPagination_MoveLabel');
                more_lavel.textContent='END';
                more_r.style.display='block';
                let hit=hit_str.textContent.replace(/,/g, '').match(/\d+/);
                let end=Math.ceil(hit/10);
                if(end>100){
                    end=100; } // 100以上は表示できない仕様
                end=end.toString();
                let jump_url=window.location.href.split('?')[0] + q_str + '&p=' + end;
                more_r.onclick=function(e){
                    event.preventDefault();
                    location.href=jump_url; }}}}



    back_sw();

    function back_sw(){
        let box=document.querySelector('.PcNavigationSearch');
        if(box){
            let help=
                '<p id="asr_help">？</p>';
            if(!box.querySelector('#asr_help')){
                box.insertAdjacentHTML('afterbegin', help); }

            let sw_=
                '<p id="back_blog">⏏</p>'+
                '<p id="sw_tooltip">ブログTOPへ</p>';
            if(!box.querySelector('#back_blog')){
                box.insertAdjacentHTML('beforeend', sw_); }

            let asr_help=box.querySelector('#asr_help');
            if(asr_help){
                asr_help.onclick=function(){
                    let help_url='https://ameblo.jp/personwritep/entry-12758463897.html';
                    let help_option="top=0, left=0, width=800, height=800, noopener"
                    window.open(help_url, null, help_option); }}

            let back_blog=box.querySelector('#back_blog');
            back_blog.onclick=function(){
                location.href='https://ameblo.jp/' + blogDB[0][1]; }}}



    let user_id=get_userid(1);

    if(user_id){
        let search_box_react=document.querySelector('#react-autowhatever-1');
        if(search_box_react){
            search_box_react.remove(); }
        let search_button=document.querySelector('.PcSearchForm_Button');

        search_button.addEventListener('click', function(e){
            let input_box=document.querySelector('.PcSuggestForm_Input').value
            if(input_box!=''){
                location.href='https://search.ameba.jp/search/entry/' + input_box + user_id; }
            e.preventDefault();
            e.stopPropagation(); }, false); }


    function get_userid(n){
        let this_url=location.href;
        let index_after=this_url.indexOf('.html?aid=');
        let caption=document.querySelector('.PcEntryList_Caption');

        if(index_after==-1){ // ブログ内検索から出た時 何もしない
            if(caption){
                caption.textContent='ブログ記事';
                caption.style.color='#298538';
                caption.style.background='transparent'; }}
        else{
            if(caption){
                caption.textContent='ブログ内検索';
                caption.style.color='#fff';
                caption.style.background='#2196f3'; }
            let user_id_a=this_url.slice(index_after);
            let index_before=user_id_a.indexOf('&p=');
            let user_id;
            if(index_before==-1){
                user_id=user_id_a; }
            else{
                user_id=user_id_a.substring(0, index_before); }
            if(n==1){
                return user_id; }
            else if(n==0){
                user_id=user_id.replace('.html?aid=', '');
                return user_id; }}}

} // search_next



function in_view(){
    let style=
        '<style class="sty0">'+
        '.PcNavigationSearch { position: relative; }'+
        '.AmebaLogo { width: 100px; }'+
        '.PcNavigationSearch_Logo > img { width: 36px; }'+
        '.PcSearchForm_Button { width: 80px; }'+
        '#asr_help { position: absolute; top: 12px; left: -35px; '+
        'font: bold 16px/21px Meiryo; height: 17px; padding: 1px 2px 2px 3px; '+
        'color: #fff; border-radius: 30px; background: #666; cursor: pointer; }'+
        '#back_blog { font-size: 32px; line-height: 26px; height: 26px; padding: 4px; '+
        'margin-left: 20px; cursor: pointer; border: 1px solid #fff; border-radius: 6px; '+
        'color: #fff; background: #2196f3; }'+
        '#sw_tooltip { position: relative; left: -165px; white-space: nowrap; '+
        'font-size: 14px; padding: 4px 10px 0; border: 1px solid #ccc; background: #fff; '+
        'box-shadow: 4px 4px 6px rgba(0, 0, 0, 0.5); display: none; }'+
        '#back_blog:hover + #sw_tooltip { display: block; }'+
        '.PcEntryList_Caption { padding: 5px 10px 2px !important; '+
        'margin: 0 10px 6px 0 !important; }'+
        '.PcResultPagination { position: relative; padding: 0 0 4px 140px !important; }'+
        '.PcResultPagination_MoreLink { font-weight: bold; display: none }'+
        '.PcEntryListItem_Link { position: relative; height: 75px; }'+
        '#history_reset { position: absolute; left: 0; padding: 2px 6px 0; cursor: pointer; '+
        'color: #fff; border: 1px solid #fff; border-radius: 4px; background: #009688; }'+
        '#edit { position: absolute; left: 70px; padding: 2px 6px 0; cursor: pointer; '+
        'color: #fff; border: 1px solid #fff; border-radius: 4px; background: #72adc8; }'+
        '#sw_tooltip2, #sw_tooltip3 { position: absolute; top: -39px; left: 0; z-index: 2; '+
        'font-size: 14px; padding: 5px 10px 2px; border: 1px solid #ccc; '+
        'background: #fff; box-shadow: 4px 4px 6px rgba(0, 0, 0, 0.5); display: none; }'+
        '#history_reset:hover + #sw_tooltip2 { display: block; }'+
        '#edit:hover + #sw_tooltip3 { display: block; }'+
        '.PcEntryListItem_Link::before { display: none; }'+
        '.history { position: absolute; left: 10px; border: thin solid #ccc; '+
        'width: 14px; height: 14px; background: #fff; border-radius: 4px; }'+
        '</style>';

    if(!document.querySelector('.sty0')){
        document.documentElement.insertAdjacentHTML('beforeend', style); }}
