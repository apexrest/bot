# Telegram bot platform
Bot platform for Oracle Apex

## packege telegram  
```
in_chat_id INT;  -- chat id
in_message_id INT; -- messaage id 
in_text VARCHAR2(32000); -- message text 
in_phone_number VARCHAR2(100); -- phone number 
in_first_name VARCHAR2(100);  -- first name user 
in_last_name VARCHAR2(100);  -- last name user
 
 -- callback --  
 
 in_data VARCHAR2(1024); -- callback data
 
 -- bot sessions --  
 
 session_st INT; -- current step --   
 session_menu VARCHAR2(100); -- current menu --   
 
  --  webhook setup --   
    PROCEDURE setwebhook (
        p_webhook_url IN VARCHAR -- urr webhook rest endpoint --
    );   
 
  -- send message --   
    PROCEDURE sendmessage (
        p_chat_id             INT DEFAULT in_chat_id,
        p_text                IN CLOB,
        p_parse_mode          IN VARCHAR DEFAULT 'HTML',
        p_resize_keyboard     IN BOOLEAN DEFAULT true, 
        p_one_time_keyboard   IN BOOLEAN DEFAULT true,
        p_buttons_colum       IN INT DEFAULT 2
    );   
    
-- edit message --  
    PROCEDURE editmessage (
        p_chat_id             INT DEFAULT in_chat_id,
        p_message_id          INT DEFAULT in_message_id,
        p_text                IN CLOB,
        p_parse_mode          IN VARCHAR DEFAULT 'HTML',
        p_resize_keyboard     IN BOOLEAN DEFAULT true,
        p_one_time_keyboard   IN BOOLEAN DEFAULT true,
        p_buttons_colum       IN INT DEFAULT 2
    );   
 
 
-- parse incoming message  --   
    PROCEDURE in_parse (
        p_body CLOB
    );   
 
-- check user  --   
    PROCEDURE check_user (
        v_ex OUT NUMBER
    );   
 
-- reset state --   
    PROCEDURE reset_st (
        p_chat_id IN INT DEFAULT in_chat_id
    );   
-- save bot session --     
    PROCEDURE save_session (
        v_menu   IN VARCHAR2 DEFAULT NULL,
        v_st     IN INT DEFAULT 0
    );   
--   get bot session --    
    PROCEDURE get_session;  
 
    -- autorization user from app  --  
    PROCEDURE auth_pin (
        v_username IN VARCHAR2
    );  
  
  -- message from app  --   
    PROCEDURE auth_reg (
        v_username   IN VARCHAR2,
        v_app_name   IN VARCHAR2
    );  
   
 
  -- send image --   
    PROCEDURE sendimg (
        p_chat_id      INT DEFAULT in_chat_id,
        p_img_id       IN INT DEFAULT NULL, 
        p_img_url      IN VARCHAR2 DEFAULT NULL,
        p_text         IN CLOB,
        p_parse_mode   IN VARCHAR DEFAULT 'HTML'
    );
```
