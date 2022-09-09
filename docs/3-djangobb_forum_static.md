# Djangobb Forum Static

[_Documentation generated by Documatic_](https://www.documatic.com)

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log-start--->
## djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log

<!---Documatic-section-log-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log</code> code snippet</summary>

```javascript
function log() {
    if (window.console && window.console.log) {
        try {
            window.console.log(Array.prototype.join.call(arguments,''));
        } catch (e) {
            log("Error:" + e);
        }
    }
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log-end--->
<!---Documatic-section-log-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.log-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection-start--->
## djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection

<!---Documatic-section-get_selection-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection</code> code snippet</summary>

```javascript
function get_selection() {
    var txt = ''; 
    if (document.getSelection) {
        txt = document.getSelection();
    } else 
    if (document.selection) {
        txt = document.selection.createRange().text;
    }
    return txt
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection-end--->
<!---Documatic-section-get_selection-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.get_selection-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste-start--->
## djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste

<!---Documatic-section-copy_paste-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste</code> code snippet</summary>

```javascript
function copy_paste(post_id) {   
    post_div = $("div#"+post_id);
    nick = post_div.find(".username").text();
    
    txt = get_selection(); // quote selection
    if (txt == '') {
        // quote the complete post content
        // FIXME: We should get the markup here (Ajax view?)
        txt = post_div.find("p.post_body_html").text();
        txt = $.trim(txt);
    }
    txt = '[quote=' + nick + ']' + txt + '[/quote]\n';
    paste(txt);
    return false
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste-end--->
<!---Documatic-section-copy_paste-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.copy_paste-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste-start--->
## djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste

<!---Documatic-section-paste-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste</code> code snippet</summary>

```javascript
function paste(txt) {
    //textarea = $("#id_body");
    textarea = document.forms['post']['body'];
    insertAtCaret(textarea, txt);
    $("#id_body").focus();
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste-end--->
<!---Documatic-section-paste-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.paste-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret-start--->
## djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret

<!---Documatic-section-insertAtCaret-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret</code> code snippet</summary>

```javascript
function insertAtCaret (textObj, textFieldValue) {
    // log("insertAtCaret(" + textObj + "," + textFieldValue + ")");
	if (document.all) { 
		if (textObj.createTextRange && textObj.caretPos && !window.opera) { 
			var caretPos = textObj.caretPos; 
			caretPos.text = caretPos.text.charAt(caretPos.text.length - 1) == ' ' ?textFieldValue + ' ' : textFieldValue; 
		} else { 
			textObj.value += textFieldValue; 
		} 
	} else { 
		if (textObj.selectionStart) { 
			var rangeStart = textObj.selectionStart; 
			var rangeEnd = textObj.selectionEnd; 
			var tempStr1 = textObj.value.substring(0, rangeStart); 
			var tempStr2 = textObj.value.substring(rangeEnd, textObj.value.length); 
			textObj.value = tempStr1 + textFieldValue + tempStr2; 
			textObj.selectionStart = textObj.selectionEnd = rangeStart + textFieldValue.length;
		} else { 
			textObj.value += textFieldValue; 
		} 
	} 
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret-end--->
<!---Documatic-section-insertAtCaret-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.bbcode.board.insertAtCaret-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ-start--->
## djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ

<!---Documatic-section-copyQ-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ</code> code snippet</summary>

```javascript
function copyQ(nick) { 
	txt = '' 
	if (document.getSelection) {
		txt = document.getSelection()
	} else 
	if (document.selection) {
		txt = document.selection.createRange().text;
	} 
	txt = '>' + nick + ':' + txt + '\n\n'
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ-end--->
<!---Documatic-section-copyQ-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.copyQ-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret-start--->
## djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret

<!---Documatic-section-insertAtCaret-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret</code> code snippet</summary>

```javascript
function insertAtCaret (textObj, textFieldValue) { 
	if (document.all) { 
		if (textObj.createTextRange && textObj.caretPos && !window.opera) { 
			var caretPos = textObj.caretPos; 
			caretPos.text = caretPos.text.charAt(caretPos.text.length - 1) == ' ' ?textFieldValue + ' ' : textFieldValue; 
		} else { 
			textObj.value += textFieldValue; 
		} 
	} else { 
		if (textObj.selectionStart) { 
			var rangeStart = textObj.selectionStart; 
			var rangeEnd = textObj.selectionEnd; 
			var tempStr1 = textObj.value.substring(0, rangeStart); 
			var tempStr2 = textObj.value.substring(rangeEnd, textObj.value.length); 
			textObj.value = tempStr1 + textFieldValue + tempStr2; 
			textObj.selectionStart = textObj.selectionEnd = rangeStart + textFieldValue.length;
		} else { 
			textObj.value += textFieldValue; 
		} 
	} 
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret-end--->
<!---Documatic-section-insertAtCaret-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.insertAtCaret-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ-start--->
## djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ

<!---Documatic-section-pasteQ-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ</code> code snippet</summary>

```javascript
function pasteQ() {
	if (txt!='' && document.forms['post']['body']) 
	insertAtCaret(document.forms['post']['body'], txt); 
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ-end--->
<!---Documatic-section-pasteQ-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteQ-end--->

<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN-start--->
## djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN

<!---Documatic-section-pasteN-start--->
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN-start--->
<details>
	<summary><code>djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN</code> code snippet</summary>

```javascript
function pasteN(text) { 
	if (text != '' && document.forms['post']['body'])
	insertAtCaret(document.forms['post']['body'], "**" + text + "**\n");
}
```
</details>
<!---Documatic-block-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN-end--->
<!---Documatic-section-pasteN-end--->

# #
<!---Documatic-section-djangobb_forum.static.djangobb_forum.js.markup.markdown.board.pasteN-end--->

[_Documentation generated by Documatic_](https://www.documatic.com)