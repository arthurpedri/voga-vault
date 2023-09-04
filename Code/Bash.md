`|` - Pipe will send the stdout of the command into the stdin of the next: `cmdthatoutputs | cmdthatreceivestheinput`
`$$` - Will run the next command after the one before finished successfully.
`;` - Will run the next command regardless of the success of the previous one.