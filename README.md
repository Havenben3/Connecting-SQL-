# Connecting-SQL-
Code to connect C# to an SQL database and insert data

          private void InsertNewMember()
        {
            MySqlConnection insertSQl = ConnectToDB();

            string CommandText = "INSERT INTO table(column1, column2, column3, column4) " + "VALUES (@value1, @value2, @value2);";

            using (insertSQl)
            {
                MySqlCommand insertDataCommand = new MySqlCommand(CommandText, insertSQl);

                insertDataCommand.Parameters.Add("@value1", MySqlDbType.VarChar);
                insertDataCommand.Parameters["@value1"].Value = textbox1.Text;

                insertDataCommand.Parameters.Add("@value2", MySqlDbType.VarChar);
                insertDataCommand.Parameters["@value2"].Value = textbox2.Text;

                insertDataCommand.Parameters.Add("@value3", MySqlDbType.VarChar);
                insertDataCommand.Parameters["@vlaue3"].Value = texbox3;

                try
                {
                    insertDataCommand.ExecuteReader();

                    MessageBox.Show("Connection. \nInserting New User Data");

                    insertSQl.Close();
                }
                catch (Exception ex)
                {
                    MessageBox.Show(ex.Message);
                }
                finally
                {
                    if (insertSQl == null)
                    {
                        MessageBox.Show("connection failed");
                    }
                }

            }
